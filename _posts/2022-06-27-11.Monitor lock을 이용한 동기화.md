---

categories: Thread

---


### monitor lock를 이용한 동기화

1. 임계영역(critical section)과 잠금장치(monitor lock)

다른 스레드가 끼어들지 말아야하는 영역 

```java
package part2;

public class Proagram2 {

	public static void main(String[] args) {

		Runnable subMain = new Runnable() {

			@Override
			public void run() {
				print();
			}
		};
		// 스레드 그룹

		Thread th1 = new Thread(subMain);
		th1.setName("sub1");

		Thread th2 = new Thread(subMain);
		th2.setName("sub2");

		th1.start(); 
		th2.start(); 

		Thread th = Thread.currentThread();
		th.setName("Main");


		try {
			Thread.sleep(2000);
		} catch (InterruptedException e) {

			e.printStackTrace();

		}
		
		System.out.println("=====exit=====");
	}

	static Object LockIndex = new Object();// 자료형이 정수형이 아닌 오브젝트형 /객체형이면 다 가능하다
	static int gIndex = 0;// 데이터/정적영역에(모든스레드가 같이 공유한다)
	

	private static void print() {
		int index = 0;/

		Thread th = Thread.currentThread();

		for (int i = 0; i < 100; i++) {

			if (th.isInterrupted()) {
				System.err.println("요청이 들어와서 종료함");
				return;
			}

			try {
				Thread.sleep(20);
			} catch (InterruptedException e) {
				// TODO Auto-generated catch block
				System.err.println("자다가깨서 종료함."); // 자고있는데 interrupt가 처리해서 깨움
				return;

			}

			// 동시 접근하면 안되는 영역-> 임계영역(Crital Section) ex)화장실:먼저 도착하는사람이 먼저한다:잠금장치이용
			// 먼저 도착한 스레드가 잠금장치 이용
			// lock으로 잠금을 해야하는 상황
			synchronized (LockIndex) { // lock을 소유한자만 안으로 들어 올 수있다

				index++;

				gIndex++; // 오브젝트가 아님

				System.out.printf("%s[%d] : %d, index:%d,gIndex: %d\n", th.getName(), th.getId(), i + 1, index, gIndex);
			}
		}

	}
}

```
 
 ```java
sub2[15] : 96, index:96,gIndex: 192
sub1[14] : 97, index:97,gIndex: 193
sub2[15] : 97, index:97,gIndex: 194
sub1[14] : 98, index:98,gIndex: 195
sub2[15] : 98, index:98,gIndex: 196
sub1[14] : 99, index:99,gIndex: 197
sub2[15] : 99, index:99,gIndex: 198
sub1[14] : 100, index:100,gIndex: 199
sub2[15] : 100, index:100,gIndex: 200 // 번호가 빠지거나 두번 나오는 경우가 없어짐

 ```