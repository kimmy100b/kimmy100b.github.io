---
layout: post
title: "[Java] 자바로 파일 및 폴더(디렉토리) 삭제하기"
categories:
  - Java
excerpt: " "
comments: true
share: true
tags:
  - Java
  - file
date: 2021-02-09T15:34:00-0:05:00
---

프로젝트 진행 중 게시물 삭제 시 폴더 내에 저장된 첨부 파일들도 함께 삭제해야 하기에 `File.delete()`함수를 사용하게 되었다. 폴더를 삭제할 때는 하위에 파일이 하나라도 남아있으면 `File.delete()`함수가 작동되지 않기에 폴더를 삭제하기 전에 폴더 안에 있는 파일을 삭제해주는 작업을 먼저 해줘야 한다.

# 📄 파일 삭제

```java
import java.io.File;

public class FileDemo {
    public static void main(String[] args) {
        try {
            String path = "C:\\test\\test.txt"; // C 드라이브 -> test폴더 -> test.txt
            File file = new File(path); // file 생성

            if(file.delete()){ // f.delete 파일 삭제에 성공하면 true, 실패하면 false
                System.out.println("파일을 삭제하였습니다");
            }else{
                System.out.println("파일 삭제에 실패하였습니다");
            }
      } catch(Exception e) {
         e.printStackTrace();
      }
   }
}
```

# 📁 폴더 삭제

파일 삭제와 마찬가지로 폴더를 삭제해주고 싶을 경우 path를 파일 위치가 아닌 폴더 위치로 설정해주면 된다. 만약 폴더 내 파일들이 있다면, 삭제가 되지 않으니 하위 파일들을 먼저 삭제해준 후 폴더를 삭제해준다.

```java
import java.io.File;

public class FileDemo {
    public static void main(String[] args) {
        try {
            String path = "C:\\test"; // C 드라이브 -> test폴더
            File folder = new File(path); // file 생성

            while(foler.exist()){
                File[] files = folder.listFiles();

                for(File file : files){
                    file.delete(); // 하위 파일 삭제
                    System.out.println("파일이 삭제되었습니다");
                }

            }
            if(folder_list.length == 0 && folder.isDirectory()){ // 하위 파일이 없는지와 폴더인지 확인 후 폴더 삭제
                folder.delete(); // 대상폴더 삭제
                System.out.println("폴더가 삭제되었습니다.");
		    }
        } catch(Exception e) {
            e.printStackTrace();
        }
   }
}
```

# 프로젝트 내 적용한 코드

```java
@Override
public void deleteFiles(String postType, int postId) {
    String rootPath = FileSystemView.getFileSystemView().getHomeDirectory().toString(); // 바탕화면 path
    String basePath = rootPath + "/" + "uploaded" + "/" + postType + "/" + postId; // 삭제해줄 게시물의 폴더 path

    File folder = new File(basePath);
    try {
        while (folder.exists()) { // 폴더가 존재한다면
            File[] listFiles = folder.listFiles();

            for (File file : listFiles) { // 폴더 내 파일을 반복시켜서 삭제
                file.delete();
            }

            if (listFiles.length == 0 && folder.isDirectory()) { // 하위 파일이 없는지와 폴더인지 확인 후 폴더 삭제
                folder.delete();
            }
        }
    } catch (Exception e){
        e.printStackTrace();
    }
}
```

# 📎 참고

<https://coding-factory.tistory.com/284>
