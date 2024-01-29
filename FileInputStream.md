# 추가학습 by 멘토님

### **각종 자료형의 사용예제**

**byte: 파일 데이터 읽기**

```java
import java.io.FileInputStream;
import java.io.IOException;

public class ReadFileExample {
	public static void main(String[] args){
		try(FileInputStream fis = new FileInputStream("example.txt")){
				byte[] bytes = new byte[50]; //타겟 파일의 읽어올 byte 길이
				int readCount = fis.read(bytes); // read 메서드를
사용하기 위해 fis 선언

// 파일의 바이트 길이만큼 반복, 읽어서 문자형으로 캐스팅
하여 출력
				for (int i = 0; i<readCount; i++){
					System.out.print((char) bytes[i]);	
			} // 입출력 에러가 발생하면 원인을 콘솔 출력한다.
		} catch (IOException error) {
			error.printStackTrace();
			}
		}
}
```

해석 : 

- FileInputStream은 파일에서 바이트를 읽어오는 스트림을 생성하는 클래스입니다. 파일의 경로는 문자열로 지정합니다.
- readCount에는 FileInputStream으로부터 읽은 바이트의 개수가 들어갑니다.
- IOException은 입출력에 발생한 예외를 나타내는 클래스입니다.
- printStackTrace()는 예외의 발생 원인을 콘솔에 출력하는 메서드입니다.

<aside>
💡 BufferedReader 클래스는 문자열을 읽어오는 스트림 클래스입니다. Socket 클래스는 네트워크에서 데이터를 읽거나 쓰는 스트림 클래스입니다.

</aside>
