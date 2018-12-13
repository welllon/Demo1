# Activity之间的数据传递的4种方式
- 1.使用Intent传递  
  intent.putExtra（key,value）;  
  Serializable和Pacelable接口的区别简单来讲：  
  Serializable 基于反射，运行时占用内存大；  
  Pacelable 基于分解，执行效率高；
- 2.使用全局变量Application传递  
  因为application的生命周期是整个应用程序的生命周期，随着应用程序的创建而创建，销毁而销毁，所以可以在activity中把数据存进或取出application中变量的值，这样所有的activity就可以对同一个application进行操作，这里不用担心线程安全的问题。
- 3.使用静态变量  
使用静态变量传递数据的方式和application有点相似，都是通过存取固定内存对象的值来传递数据，对象中用static定义的静态成员存放在静态域中，可以通过不同引用来访问，只需在目标activity中定义静态成员变量，源activity就可以直接访问 
- 4.剪切板传递数据  
//获得剪切板单例
ClipboardManager clipboardManager = (ClipboardManager)getSystemService(Context.CLIPBOARD_SERVICE);
//添加数据到剪切板
clipboardManager.setPrimaryClip(ClipData.newPlainText(null,"内容"));
//检查剪切板是否有数据，并取出数据
if(clipboardManager.hasPrimaryClip()){
clipboardManager.getPrimaryClip().getItemAt(0).getText();
}

