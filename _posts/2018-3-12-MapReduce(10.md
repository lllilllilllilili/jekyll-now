---
layout : post
title : MapReduce(1)
---
MapReduce를 단계적으로 공부해보자.

## Large scale computing for big data
Mapreduce는 일종에 OS위에 돌아가는 프레임워크다.
Hadoop은 이론을 구현한것이다. 

## MapReduce
간단하고 강력한 인터페이스다, 자동 병렬프로그래밍, 큰 규모의 계산을 분배할때 가능하게 해준다.
PC들의 큰 cluster(분산환경처리)에 높은 수행들을 달성하는 인터페이스들이 구현에 결합되어 있다.
프로세스 데이터 처리를 특별히 map() 과 reduce() 함수를 사용한다.
MapReduce는 명령프로그램모델이고, 인터페이스를 제공하며 병렬로 처리 되기 때문에 분산 시스템인(=cluster) 도와준다.
google에 데이터가 index로 처리되어 많은 데이터를 처리하는데 MapReduce가 활용된다.
MapReduce는 한단어 같지만 따로 볼 수 있다.
Map은 Mapping 해서 Reduce 처리한다.(Reduce는 데이터를 줄여서 final data로 만든다.) 
디스크의 값을 메인메모리에 올려서 cpu가 처리하면 데이터를 읽어서 처리하기에 상당한 시간이 들면 아주 오랜 시간이 걸릴 것이다.
그래서 큰 데이터의 경우 수천개의 하드디스크에 저장하게 되는데, 빅데이터 cluster를 구현해서 리눅스서버에 많은 cluster를 묶어 모델을 구현한것이다.

## Cluster Architecture[1]
Cluster는 각각의 렉인클루져(렉이 16~64대 모여) 스위치로 묶이는데 이 스위치도 스위치로 묶는다.(성능향상을 위해서) 백보드로 (저장장치로) 설치하는 경우도 있다.
![](https://upload.wikimedia.org/wikipedia/commons/7/7c/Sun_Microsystems_Solaris_computer_cluster.jpg)

## Large-scale Computing
Large-scale computing은 시중에서 쉽게 구할 수 있다.
### 문제점
1. 계산을 어떻게 분배할 것인가?
2. 어떻게 분배된 프로그램을 쉽게 읽을 것인가?
3. 장치가 죽으면 어떻게 처리할까?
ㄴ실제로 많은 서버가 죽는다.

## Idea and solution
문제 : 데이터를 네트워크를 통해 받으면 굉장히 시간이 많이 걸림
cluster에 넣으면 분산해서 들어가는데, 네트워크 망으로 읽어야 하는데 크기가 커서 추가적인 데이터는 백보드 망으로 받는다.
핵심 요소 : 데이터가 커지면서 오버레드가 상당한 부담요소로 작용하기 때문에 읽지말고 짜놓은 코드를 바탕으로 데이터를 처리하기 위한 function을 작성하여 function 자체가 가서 실행되면 오버헤드가 줄어들 수 있을 것이다.(데이터베이스의 RDP와 유사한 방식)
죽는 데이터에 대비해서 데이터를 가져다가 복사한다.(for reliablility)
Mapreduce는 I/O 저장기능을 제공한다(cluster에 맞는, 프로세싱에 도움을 준다.)
데이터 성질에 따라 Google GFS, Hadoop HDFS가 있다.

## Storage Infrastructure
문제 : 서버가 죽으면 데이터를 어떻게 지속적으로 유지할 수 있을까?
DFS로 분산 파일 시스템을 이용한다. EX) 하둡 HDFS
이런 시스템들은 한번 쓰면 드물게 업데이트 한다. 거의 읽기만 한다.

## Distributed File System(DFS)
### chunk servers
큰데이터가 들어오면 chunk server가 자른다. 규격은 16-64M으로 잘라 Cluster에 뿌린다. (보통 chunk 3개정도가 서버에 뿌리고 3개정도 복사한다, 서버가 죽는것을 방지)
복사한 데이터를 똑같은 렉 1개, 다른 렉 1개, 복사할 렉 1개 이렇게 복사하면서 렉서버가 망해도 보장할 수 있도록 한다. (for reliability)
### Master node
수많은 서버에 대장이 되는 노드로, Master 노드라고하고 Name 노드라고 한다.
클라이언트가 마스터노드에 파일을 요청하면 마스터노드는 파일 위치를 전송하고 위치 정보를 cluster에 전송하여 cluster가 데이터를 가지고 온다.

각각 다른 chunk 서버, 데이터 노드에 적당하게 3개 카피해 둔다.

## Programming Model: MapReduce
간단하게 인기 웹서버를 찾고 싶으면 logs를 가져와서 단어를 count해서 Maxcount된것이 인기있는 웹을 찾을 수 있다.

## Task : Word Count
words(doc.txt) | sort | uniq -c
데이터 한줄 던져줘서(읽은뒤) -> sort -> 유니크 단어를 뽑아서 c하면 count 한다.
그 결과를 뿌린다.
단어를 뽑아내고 (Map해서 하는일) sorting하고 결과를 뿌린다.

## MapReduce : overall procedures
1. 데이터를 연속적으로 읽어오고
2. Map으로 인터페이스에 맞게 프로그래머가 작성하며(추출한다)
3. key를 통해서 그륩으로 sort하거나 shuffle
4. 데이터를 가져와서 Reduce(통합, 요약, 걸러내거나 변형시킨다)
5. 결과값을 쓴다.

## MapReduce: logical view
Maap에는 Input, Output function을 제공하는데 Input으로 key-value pairs로 제공하게 된다. 이렇게 만들어진 중간위치에 결과도 key-value의 pairs의 형태를 띈다.

Reduce에는 Mapper에서 나온 Output을 Reduce의 Input이 된다.
중간위치의 결과가 Group by key로 묶여서 같은 key가 여러개가 되어 sorting에서 하나로 합쳐놓고 이것을 reduce로 output key-value pairs의 결과를 내게 된다. 
Reduce가 내놓은 결과값이 final 결과값이다.

## MapReduce:physical view
Hadoop HDFS의 input은 Hadoop Cluster를 Chunk server로 잘라서 (64bit 데이터로 잘라서(Input split)) map에 하나의 chunk를 할당 sort한뒤 Intermidiate(중간결과)를 복사하고(이때 서버가 죽을것을 염려하여 여분의 복사분을 만듬) 다른 map에서 온 cunk를 sort해서 merge를 한뒤 reduce로 들어가 최종 결과값은 Reduce 당 한 결과값이 나온다.(output HDFS)

## More Specifically
mapper, reduce는 보통 프로그래머가 작성한다.

## MapReduce : Word Count
전반적인 MapReduce가 Word Count를 처리하는 개략적인 과정을 보면
Input으로 64메가 로 청크되었다고 가정하고, 청크 서버가 같은 사이즈로 자른다.
splitting을 하는데 k1,v1(파일이름, 64메가한줄) 한뒤 Mapping (local에서 일어난다)
List(파일이름,카운트개수)로 표시한다. Mapping에서는 values는 count값을 던진다.
Shuffling 단계에서는 (파일이름, 같은 단어를 모두 count해서 표시해준다(convined됨)) Shuffling단계는 네트워크 과정이다.(Sorting, merge)
Reducing은 Suffling에서 convined 된 count값을 모두 합쳐서 보여주고, Final Result을 내보낸다. (Reducing당 결과값은 하나다.)
*Mapper는 동시에 돌아가기때문에 병렬화 되었다고 한다. 

## Word Count Using MapReduce
map(key, value): 
*key : 문서이름, value : 문서의 단어
reduce(key, values):
*key : 단어 value : count한 값을 저장함
* map, reduce는 Hadoop Interface를 제공

## MapReduce : Environment
다음의 사항을 고려한다.
1. 입력에 대한 하드디스크의 파티션 부분을 얼마나 할당할 건가.
2. Scheduling
3. key를 그륩으로 묶어서 수행
4. 컴퓨터가 죽는것을 처리해야한다.
5. 컴퓨터간에 커넥션이 요구되는것을 관리해야한다.

## MapReduce : A diagram
큰 용량의 데이터가 Input으로 들어오면 Chunk server가 자르고 splitting 단계를 거쳐서 Mapping 을 하게되는데 List(k2,v2) 형식으로 구성된다. Group by key로 묶어서 sorting, shuffling 한뒤 묶여진 데이터를 Reduce 단계를 거쳐서 각각 마다 하나의 결과물이 계산되어 나온다.

## MapReduce:Parallelism
모든 단계는 많은 일들이 병렬적으로 처리된다.

## MapReduce:Workflow
### 프로그래머가 구현하는것
Map 과 Reduce
Input과 Output의 format

## Data Flow
Input값과 final output 값은 FS(File system)에 분배되서 저장된다.
리눅스위에 렉서버가 돌아가면 DFS(Data File System)를 사용하는데 자기자신의 Local File System위에 돌게된다.(Mapping 단계)
DFS는 Chunk server를 통해 64메가 기준으로 쪼개서 저장한다.(Input data에 대해서)
Output DFS의 형태라 찾기가 쉽지 않다.(Key-values)
Map이 중간결과값을 자기자신서버에 적는다.(DFS가 Local System 위에 돌아간다.)
Reduce 네트워크를 통해서 Local System에 있는것을 가져옴. sort후 Reduce값을 던진다.
## Coordination : Master
Master Node는 모든 Scheduled를 담당하고 있고, 클라이언트는 Map이 끝나면 Master Node에게 알린다. 이걸 알리면 Master Node가 Reduce로 전달한다.
수많은 서버들이 죽는데, Ping을 던져서 모든노드들을 대상으로 체크한다.
ACK를 받아서 확인하거나, 프로그래머가 TIMEOUT을 걸어서 응답이 안오면 Master노드가 해당 서버에 대한 일을 다른 서버에게 할당한다.

## Dealing with Failures
### Worker failure
ping으로(Heartbeat) 죽은 서버를 발견시 모든일을 전부 없애고 다시 실행한다.
Map이 일이 끝나도 다시 실행하는 경우가 있다. 왜냐하면 local system에서 map이 실행되기 때문에 값을 자기자신이 가지고 있기 때문이다.
Reduce는 끝나면 끝난것이지만, 안끝났다면 다시 실행하면된다.
### Master failure
Master Node가 죽으면 대처방법이 초기에는 구현되지 않았지만 요즘에는 두번째 Master Node가 있기도 하다.
CheckPoint로 DFS 과정에서의 상태를 백업받아 놓고 Master Node가 죽으면 이 상태로 리두로 돌아가는듯 싶다.

## How many Map and Reduce jobs?
Map은 cluster의 node의 수보다 많아야 한다.
Chunk 하나당 Map 한개 할당된다.
load balancing을 통해 worker failures 가 생기면 빠르게 복구한다.
Reduce는 Map보다 통상적으로 작다.

## Task Granularity & Pipelining
오류 복구를 위한 시간을 최소화 한다.
map이 실행될때 pipeline shuffling을 할 수 있다.
동적인 로드 밸런싱보다 좋다.
mapper의 아웃풋이 Reduce의 인풋으로 들어간다.
병렬시스템이고 성능에 좋다.

## Refinements : Locality
Map은 데이터를 읽을때 다른 곳의 데이터를 읽어오면 효율이 떨어진다.
그래서 갖고 있는 local위치에 맞는 데이터를 가져온다.(Master node가 실행하며 스케쥴링 장치로 분배한다)
Local data를 우선적으로 Map에 할당하나 없으면 가까운 거리에 데이터를 가지도록 담당한다. 왜냐하면 네트워크가 혼잡한것을 막기 위함이다. (Master Node가 실행)

## Refinements : Backup Tasks
Map의 일이 끝나지 않는다, blocking이 걸리면 경쟁해서 백업하게 되는데 이 과정을 Name Node가 체크하게 된다. Map을 두개 실행시켜서(같은것을) 처리과정에서 더 느린쪽을 삭제한다. 시간을 단축시킬 수 있다.

## Reference
[1] https://en.wikipedia.org/wiki/Computer_cluster
MapReduce에 관한 Print