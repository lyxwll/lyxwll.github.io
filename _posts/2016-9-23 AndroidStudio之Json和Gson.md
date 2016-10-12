##AndroidStudio之数据解析--- Json和Gson         


###Json    

**Json(Javascript Object Notation)**是一种轻量级的数据交换格式。xml这种数据交换格式解析比较复杂，而且需要编写大段的代码，所以客户端和服务器的数据交换格式往往通过json来进行交换。尤其是对于web开发来说，json数据格式在客户端直接可以通过javascript来进行解析。      
 
**数据格式** [http://www.json.org/json-zh.html](http://www.json.org/json-zh.html)     

- (1).JsonObject对象：以**(key/value)对**形式存在的无序的jsonObject对象，一个对象以“{” 开始，“}”结束。每个“名称”后跟一个“:” ； **‘名称/值’ 对**之间使用“,” 分隔。key值必须要是string类型。
- (2). Json数组： 有序的value的集合，这种形式被称为是jsonArray，数组是值（value）的有序集合。一个数组以“[” 开始，“]”结束。值之间使用“,”（逗号）分隔。      
 在这两种数据结构下，值（value）可以是双引号括起来的字符串（string）、数值(number)、true、false、 null、对象（object）或者数组（array）。这些结构可以嵌套。        
![img](/img/2016.10.11/0001.png)       

![img](/img/2016.10.11/0002.png)

**Json应用**            
libs：[http://sourceforge.net/projects/json-lib/files/json-lib/](http://sourceforge.net/projects/json-lib/files/json-lib/)           

- (1). Java EE 5.0下导入如下包：         
![img](/img/2016.10.11/0003.png)

- (2). 服务器端      
关于toString的补充    
[http://blog.163.com/tangyang_personal/blog/static/4622961320082268951289/](http://blog.163.com/tangyang_personal/blog/static/4622961320082268951289/) 
![img](/img/2016.10.11/0004.png)

JsonService.java 

**Json的几种数据格式：**        

```java          
/**
 * 进行Json收发过程中的对应对象转换，即提供Json中的value    
 * @author FanFF       
 */   
public class JsonService {

    public JsonService() {
        super();
    }

    /**value是字符串
     * {key:value, key:value,...}
     * {"address":"beijing","id":1001,"name":"jack"}
     * @return
     */
    public Person getPerson() {
        Person person = new Person(1001, "jack", "beijing");
        return person;
    }

    /**value是数组[],数组又是{key:value}
     * {key:[{key:value},{key:value},...]}
     * [{"address":"beijing","id":1001,"name":"Smith"},{"address":"shanghai","id":1002,"name":"David"}]
     * @return
     */
    public List<Person> getlistPerson() {
        List<Person> list = new ArrayList<Person>();
        Person person1 = new Person(1001, "Smith", "beijing");
        Person person2 = new Person(1002, "David", "shanghai");
        list.add(person1);
        list.add(person2);
        return list;
    } 

    /**
     * {key:[value,value,value...]}
     * {"person":["beijing","shanghai","guangzhou"]}
     * @return
     */
    public List<String> getListString() {
        List<String> list = new ArrayList<String>();
        list.add("beijing");
        list.add("shanghai");
        list.add("guangzhou");
        return list;
    }

    /**
     * {key:[{key:value , key:value,...},{key:value, key:value...}]}
     * {"person":[{"id":1001,"address":"beijing","name":"Smith"},{"id":1002,"address":"David","name":"rose"}]}
     * @return
     */
    public List<Map<String, Object>> getListMaps() {
        List<Map<String, Object>> list = new ArrayList<Map<String, Object>>();
        Map<String, Object> map1 = new HashMap<String, Object>();
        map1.put("id", 1001);
        map1.put("name", "Smith");
        map1.put("address", "beijing");
        Map<String, Object> map2 = new HashMap<String, Object>();
        map2.put("id", 1002);
        map2.put("name", "David");
        map2.put("address", "David");
        list.add(map1);
        list.add(map2);
        return list;
    }
}
```

JsonTools.java:    

```Java   
    /** @param key   
     * @param value   
     * @return Json对象的字符串表示  
     */   
    public static String createJsonString(String key, Object value){
        JSONObject jsonobject = new JSONObject(); 
        jsonobject.put(key, value);
        return jsonobject.toString();
    }
```

- (3). Android端       
![img](/img/2016.10.11/0005.png)       
在AndroidMainfest.xml中添加网络配置，如下:       
![img](/img/2016.10.11/0006.png)       

但是在4.0之后仍然会出现如下错误：   
![img](/img/2016.10.11/0007.png)          

原因可能是：因为Http请求写在了主线程里， 在4.0之后在主线程里面执行Http请求都会报这个错，大概是怕Http请求时间太长造成程序假死的情况。
解决方法：[http://www.tuicool.com/articles/MvmeYr](http://www.tuicool.com/articles/MvmeYr)      

**方法一**：在主线程中直接忽略，强制执行。（不推荐这种方法，但是该方法修改起来简单）。 
在MainActivity文件的 setContentView(R.layout.activity_main)下面加上如下代码： 
```Java
if (android.os.Build.VERSION.SDK_INT > 9) {       
StrictMode.ThreadPolicy policy = new  StrictMode.ThreadPolicy.Builder().permitAll().build();    
StrictMode.setThreadPolicy(policy);     
}     
```

**方法二**：启动另一个线程执行网络连接任务，比如使用Thread、Runnable、Handler(推荐使用这种方法)。     
建立网络连接        
```Java     
 /**    
  * 建立网络连接                  
  */          
public class HttpUtils {      

    public HttpUtils() {       
    }      
  
    /**
     * 通过URL获取服务器端通过JSon传来的数据
     * @param url_path
     * @return
     */
    public static String getJsonContent(String url_path){
        String jsonString = "";
        try {
            URL url = new URL(url_path);
            HttpURLConnection connection = (HttpURLConnection) url.openConnection();
           // 设置连接属性
            connection.setConnectTimeout(3000);// 超时
            connection.setRequestMethod("GET");
            connection.setDoInput(true);// 输入流
            int code = connection.getResponseCode();
            if (code == 200){
               jsonString = changeInputStream(connection.getInputStream());
            }
        } catch (MalformedURLException e) {
            e.printStackTrace();
        } catch (IOException e) {
            System.out.println("获取网络连接失败!");
        }
        return jsonString;
    }

    /**
     * 将输入流转换为字符串
     * @param inputStream
     * @return
     */
    private static String changeInputStream(InputStream inputStream) {
        String jsonString = "";
        ByteArrayOutputStream outputStream = new ByteArrayOutputStream();
        int len = 0;
        byte[] data = new byte[1024];
        try {
            while ((len = inputStream.read(data))!=-1){// 从inputsteam流中读取数据到data数组中
                outputStream.write(data, 0, len);// 将已经写入到data数组中的字节流写入到outputStream流中
            }
            // 利用输入流的toByteArrar()方法转换成字节数组
            // 然后利用String的构造函数
            jsonString = new String(outputStream.toByteArray());
        } catch (IOException e) {
            e.printStackTrace();
        }
        return jsonString;
    }
}
````

```Java          
    /** 将输入流转换为字符串        
     * @param inputStream         
     * @return         
     */       
    private static String changeInputStream(InputStream inputStream) {     

        String jsonString = "";
        ByteArrayOutputStream outputStream = new ByteArrayOutputStream();
        int len = 0;
        byte[] data = new byte[1024];
        try {
            while ((len = inputStream.read(data))!=-1){// 从inputsteam流中读取数据到data数组中
                outputStream.write(data, 0, len);// 将已经写入到data数组中的字节流写入到outputStream流中
            }
            // 利用输入流的toByteArrar()方法转换成字节数组
            // 然后利用String的构造函数
            jsonString = new String(outputStream.toByteArray());
        } catch (IOException e) {
            e.printStackTrace();
        }
        return jsonString;
    }
```

按照服务器端的封装对Json字符串进行各种格式的数据解析  
```Java         
/**    
 * 完成对json数据的解析       
 */   

public class JsonUtils {   

    public JsonUtils() {
    }

    /**
     *例如：{"person":{"address":"beijing","id":1001,"name":"jack"}}
     * @param key 即 person
     * @param jsonString 即{"person":{"address":"beijing","id":1001,"name":"jack"}}
     * @return
     */
    public static Person getPerson(String key, String jsonString){
        Person person = new Person();
        try {
            JSONObject jsonObject = new JSONObject(jsonString);// 通过jsonString创建jsonobject
            JSONObject personObject = jsonObject.getJSONObject(key);// 通过key获取value对象
            // 通过key获取的value设置Person对象的各个属性字段
            person.setId(personObject.getInt("id"));
            person.setName(personObject.getString("name"));
            person.setAddress(personObject.getString("address"));
        } catch (JSONException e) {
            e.printStackTrace();
        }
        return person;
    }

    /**
     * {"persons":[{"address":"beijing","id":1001,"name":"Smith"},{"address":"shanghai","id":1002,"name":"David"}]}
     * @param key
     * @param jsonString
     * @return
     */
    public static List<Person> getPersons(String key, String jsonString){
        List<Person> list = new ArrayList<Person>();
        try {
            JSONObject jsonObject = new JSONObject(jsonString);
            JSONArray jsonArray = jsonObject.getJSONArray(key);// json数组
            for (int i = 0; i < jsonArray.length(); i++){
                JSONObject jsonObjectTemp = jsonArray.getJSONObject(i);
                Person person = new Person();
                person.setId(jsonObjectTemp.getInt("id"));
                person.setName(jsonObjectTemp.getString("name"));
                person.setAddress(jsonObjectTemp.getString("address"));
                list.add(person);
            }
        } catch (JSONException e) {
            e.printStackTrace();
        }
        return list;
    }

    /**
     * {"liststring":["beijing","shanghai","guangzhou"]}
     * @param key
     * @param jsonString
     * @return
     */
    public static List<String> getList(String key, String jsonString){
        List<String> list = new ArrayList<String>();
        try {
            JSONObject jsonObject = new JSONObject(jsonString);
            JSONArray jsonArray = jsonObject.getJSONArray(key);
            for (int i = 0; i < jsonArray.length(); i++){
                String msg = jsonArray.getString(i);
                list.add(msg);
            }
        } catch (JSONException e) {
            e.printStackTrace();
        }
        return list;
    }

    /**
     * {"listmap":[{"id":1001,"address":"beijing","name":"Smith"},{"id":1002,"address":"David","name":"David"}]}
     * @param key
     * @param jsonString
     * @return
     */
    public static List<Map<String, Object>> listKeyMaps(String key, String jsonString) {
        List<Map<String, Object>> list = new ArrayList<Map<String, Object>>();
        try {
            JSONObject jsonObject = new JSONObject(jsonString);
            JSONArray jsonArray = jsonObject.getJSONArray(key);
            for (int i = 0; i < jsonArray.length(); i++){
                JSONObject jsonObjectTemp = jsonArray.getJSONObject(i);
                Map<String, Object> map = new HashMap<String, Object>();
                Iterator<String> iterator = jsonObjectTemp.keys();
                while (iterator.hasNext()){
                    String json_key = iterator.next();
                    Object json_value = jsonObjectTemp.get(json_key);
                    if (json_value == null){
                        json_value = "";
                    }
                    map.put(json_key, json_value);
                }
                list.add(map);
            }
        } catch (JSONException e) {
            e.printStackTrace();
        }
        return list;
    }
}

````   

对应的服务器端类:      
```Java           
/**  
 * json字符串对应的服务器对象  
 * Created by FanFF on 2016/2/3.     
 */   
public class Person {       

    private int id;
    private String name;
    private String address;

    public Person() {
        // TODO Auto-generated constructor stub
    }
    public Person(int id, String name, String address) {
        super();
        this.id = id;
        this.name = name;
        this.address = address;
    }
    
    public int getId() {
        return id;
    }
    public void setId(int id) {
        this.id = id;
    }

    public String getName() {
        return name;
    }
    public void setName(String name) {
        this.name = name;
    }

    public String getAddress() {
        return address;
    }
    public void setAddress(String address) {
        this.address = address;
    }

    //toString重写用以在调用该对象的时候得到想要输出的信息
    @Override
    public String toString() {
        return "Person [address=" + address + ", id=" + id + ", name=" + name
                + "]";
    }
}
```     

简单分析：服务端写入数据到相应的对象的属性中,客户端通过HttpUtils中的相应类获取网络中字节流并转化为字符串，然后解析字符串中的数据，提取该数据设置成相应的对象的属性。     

###二、Gson
**介绍**   
**Gson**这个Java类库可以把Java对象转换成JSON，也可以把JSON字符串转换成一个相等的Java对象。Gson支持任意复杂Java对象包括没有源代码的对象。  
 
**本质说明**        
使用Gson主要是在解析Json时利用了泛型和反射机制，避免了反复的复杂的迭代和set属性字段。这里就不做说明了。   
 
JSON和Gson的详细代码参加如下：         
[https://github.com/herdyouth/JsonDemo](https://github.com/herdyouth/JsonDemo ) 
[https://github.com/herdyouth/GsonDemo](https://github.com/herdyouth/GsonDemo)        
或者            
[https://yunpan.cn/cxptw4A3WEtx2](https://yunpan.cn/cxptw4A3WEtx2) 访问密码 ee61           




