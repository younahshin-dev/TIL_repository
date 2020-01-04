# Collection FrameWork 

## ArrayList
- 가장 많이 이용되는 컬렉션 클래스, List 인터페이스를 구현하기 때문에 데이터의 저장순서가 유지되고 중복을 허용한다.
1.데이터를 순차적으로 저장, 배역에 더이상 저장할 공간이 없으면 보다 큰 새로운 배열을 생성해서 기존의 배열내용을 복사한다음 저장한다.

## LinkedList
- 배열은 구조가 간단하며 사용하기 쉽고 데이터를 읽어 오는데 걸리는 시간이 가장 빠르다는 장점을 가지고 잇지만 단점도 있다.
>1. 크기를 변경할 수 없다.
>2. 비순차적인 데이터의 추가 또는 삭제에 시간이 많이 걸린다.
>
>이러한 단점을 보완하기 위해 링크드 리스트라는 자료구조가 고안되었다.

링크드리스트는 이동방향이 단방향이기 떄문에 이전데이터에 대한 접근이 어렵다. -> 더블링크드리스트-> 더블링크드 리스트의 접근성을 보다향상시킨 것이 '더블 써큘러 링크드 리스트)

## Stack 과 Queue
- stack(Last In First Out) ex) 수식계산, 수식괄호검사, 워드프로세서의 undo/redo, 웹브라우저의 뒤로/앞으로
- queue(First In Last Out) ex) 최근 사용문서, 인쇄작업 대기목록, 버퍼(buffer)

## PriorityQueue
- queue의 인터페이스이ㅡ 구현체 중의 하나, 저장한 순서에 관계 없이 우선순위(숫자가 작을수록 우선순위가 높음)가 높은것부터 꺼낸다.
- 저장공간으로 배열을 사용하며, 각 요소를 heap이라는 자료구조의 형태로 저장한다. 
*heap은 이진트리의 한종류로 가장큰 값이나 가장 작은 값을 빠르게 찾을 수 있다는 특징이 있다. != JVM heap

## Deque(Double-Ended Queue)
- Queue의 변형 형태 양쪽 끝에 추가/삭제가 가능하다. 구현체로는 ArrayDeque, LinkedList등이 있다.
- stack과 queue를 하나로 합쳐놓은 것과 같다.
 
  |     DEQUE     |     Queue     |     Stack     |
  |---------------|:-------------''-|--------------:|
  |  offerLast()  |    offer()    |    push()     |
  |  pollLast()   |       -       |     pop()     |
  |  pollFirst()  |     poll()    |       -       |
  |  peekFirst()  |     peek()    |       -       |
  |   peekLast()  |       -       |    peek()     |
  
## Iterator
 - 저장된각요소에접근하는기능을 가진 인터페이스
 - Collection 인터페이스에는 'Iterator(Itorator를 구현한 클래스의 인스턴스)'를 반환하는 iterator()를 정의하고 있다.
 
 ```java
 public interface Iterator {
  boolean hsNext();
  Object next();
  void remove();
 }
 
 public interface Collection {
  ...
  public Iterator iterator();
  ...
 }
 ``` 
# collection
**1. Synchronized Collection**
In multi-thread programming, shared Object is needed Synchronization for remain consistency 
because many threads can approach an Object at the same time.
  
>ex) static Collection synchronizedCollection(Collection c)
  
**2. Unmodifiable Collection**
Unmodifiable Collection is Used for protecting data which is saved at collection
  
>ex) static Collection unmodifiableCollection(Collection c)
  
**3. Singleton Collection**
  When you wanna make a collection which can save only one object. you can use Singleton Collection
  
>ex) static List singletonList(Object o)
  
**4. Making Collection that can save only one kind of object**
  
>ex) 
List list = new ArrayList();
List checkedList = checkedList(list ,String.class); //only String object can be saved

      
      
      
      
