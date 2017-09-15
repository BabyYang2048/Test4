# Test4   ---内部存储文件操作
    1.掌握向内部存储卡上写入文件和读取文件的方法。
    2.编程实现向内部存储卡写入学号、姓名等信息并读取、显示这些信息。
    
      
      关键代码
      ----写入
          OutputStream out = null;
          FileOutputStream fileOutputStream = null;
         
          fileOutputStream = openFileOutput("MyFileName.txt", MODE_PRIVATE/*MODE_APPEND*/);
          //openFileOutput将数据存到具体指定文件，第一个参数是文件名，第二个参数是文件的操作方式,这个方法返回的是FileOutputStream对象
          out = new BufferedOutputStream(fileOutputStream);
          String all = editText1.getText().toString();
          out.write(all.getBytes(Charset.forName("UTF-8")));
           
      ----读取
          InputStream in = null;
          BufferedReader reader = null;
          String c = "";
         
          FileInputStream fileInputStream = openFileInput("MyFileName.txt");
          reader = new BufferedReader(new InputStreamReader(fileInputStream));
          StringBuilder stringBuilder = new StringBuilder();
          while((c=reader.readLine())!=null){
              stringBuilder.append(c);
          }
          
          
     关于写入读取这部分最让我头大的就是很多不同含义字节流，对于初学者经常会搞混。
     
     我在最初写这部分代码的时候遇到了一个问题：
            在显示的数据中有汉字，读出显示的时候就产生了乱码。
     ---问题原因：
        在读取的时候将字节流先用int型读出在转换为char型，在转换过程中就出现了问题。
     ---解决办法：
        在读取数据时设置String型变量，并采用readline()方法读取。
     
     大家在自己尝试的时候记得注意这方面的问题~~~
     
          
     
                   
                   
