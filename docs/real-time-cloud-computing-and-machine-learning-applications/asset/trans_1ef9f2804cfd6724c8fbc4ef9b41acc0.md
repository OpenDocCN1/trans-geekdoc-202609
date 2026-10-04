

# 基于云的实时... 的数据捕获与客户端架构 ... 283

- 设置下一个要发送到下一个“Key”值的索引。
- 允许通过设置为 `true` 的 `Clickable()` 方法来使用切换开关。

该线程的代码在列表 4.15 所示。

# 列表 4.15. 从云端检索最后一个索引的线程

```java
// 获取云端上记录的最后一个索引
private final Runnable getNumberOfItems = new Runnable() {
    public void run() {
        // 连接云端数据库
        try {
            // 创建新的 CloudClient 实例，通过端点的 URL 
            // 连接到 Cloudant 服务器
            Client client = ClientBuilder.url(newURL("https://8118bf82-4f01-4173-be30-76ff8be7d7-bluemix.cloud.com"));
            // 设置客户端连接的用户名
            client.username("apikey-f412e25478b7413a8c26dbafaf1b8dc");
            // 设置客户端连接的密码
            client.password("ee7af59364bde695efabad72255fab70da9a8");
            // 根据用于构建客户端构建器的端点构建 CloudClient 
            // 实例
            System.out.println("成功连接到云端...");
        } catch (IOException e) {
            System.out.println("访问云端出错:" + e);
        }
        // 访问云端参数数据库：
        Database db = client.database("androidcloudparameters", false);
        System.out.println("尝试从数据库读取所有记录...");
        // 降序检索所有键的查询：
        String query = "{"selector":{"Key":{"$gt":0}}","fields":["Key"],"sort":{"Key":{"$desc":true}}"}}";
        // 使用 QueryResult 对象执行查询
        QueryResult<LinkedTreeMap> queryResult = (QueryResult<LinkedTreeMap>)db.query(query, LinkedTreeMap.class);
        // 获取 List 对象中的结果：
        List<LinkedTreeMap> list = queryResult.getDocs();
        // 检查数据库是否已包含：
        if (list.size() > 0) {
            // 从列表中获取第一个 Key 值
            numberOfItems = (double)list.get(0).get("Key");
            // 如果数据库为空，则将项目数量设置为 0
            numberOfItems = 0.0;
        } else {
        }
    }
}
```

```java
System.out.println("数据库中的文档数量为:" +
numberOfItems);
// 后续记录必须具有 (最后一个键 + 1) 作为其键
idx = (int) numberOfItems + 1;
System.out.println("设置新记录的索引为:" + idx);
// 启用切换/开关以进行点击
cloudSwitch.setClickable(true);
} catch (Exception e) {
    System.out.println("获取项目数量出错:" + e.toString());
}
```

## 4.3.6. onCreate() 方法中的流量监控

`onCreate()` 方法在 Android Studio 中构建 Android 项目时自动创建，专门用于 `MainActivity.java` 类初始化期间发生的过程，即该类启动时。它包含了以下必要功能。

- 将布局上的组件映射到它们相应的变量。
- 指定折线图设置。
- 设置轴配置和图例的选项。
- 配置旋转器（spinner）以包含多个选择并积极监听更改。
- 查找要监控参数的第一组值。
- 调用“监控”、“停止”和“转分析”按钮。

本节中的代码属于 `onCreate()` 方法，并与列表 4.16 到 4.21 定义的按钮调用相关。

> 列表 4.16. Monitor_App 中 onCreate() 方法概述

```java
@Override
protected void onCreate(Bundle savedInstanceState) {
    super.onCreate(savedInstanceState);
    setContentView(R.layout.activity_main);
    // 此处包含了列表 4.17 到 4.21
}
```

### 4.3.6.1. 初始化组件

上述在 `MainActivity.java` 类和 XML 文件中定义的组件通过初始化过程进行链接，该过程本质上是获取 UI 中的组件并可以通过程序进行交互。这是 `onCreate()` 内部执行的首个操作。

### 列表 4.17. MainActivity 中 onCreate() 中的组件初始化

```java
// 将变量映射到相应的布局对象：
ipaddress = findViewById(R.id.EDT1); // 用于存储 IP 地址的变量
cloudSwitch = findViewById(R.id.cloudSwitch); // 获取云端开关的变量
monitorButton = findViewById(R.id.monitorButton); // 监控按钮变量
stopButton = findViewById(R.id.stopButton); // 停止按钮变量
algoButton = findViewById(R.id.algo); // 分析菜单变量
downloadButton = findViewById(R.id.downloadButton); // 下载按钮变量
RX = findViewById(R.id.textView1); // 用于存储 Wi-Fi 下载速度的变量
TX = findViewById(R.id.textView2); // 用于存储 Wi-Fi 上传速度的变量
RXP = findViewById(R.id.textView3); // 用于存储接收包数量的变量
TXP = findViewById(R.id.textView4); // 用于存储发送包数量的变量
WiFiSig = findViewById(R.id.textView5); // 用于存储 Wi-Fi 信号的变量
MRX = findViewById(R.id.textView6); // 用于存储 LTE 下载速度的变量
MTX = findViewById(R.id.textView7); // 用于存储 LTE 上传速度的变量
cloudSwitch.setClickable(false); // 启动时临时禁用开关
```

由于 `MainActivity.java` 类和 XML 文件中定义的上述组件通过初始化过程进行链接，该过程本质上是获取 UI 中的组件并可以通过程序进行交互。这是 `onCreate()` 内部执行的首个操作。

## 4.3.6.2. 获取初始数据

由于 `onCreate()` 方法在应用程序启动时处理，Wi-Fi 和 LTE 的初始接收和发送字节数通过上述 `TrafficStats` 类获取。

### 列表 4.18. 使用 TrafficStats 获取初始数据

```java
// 初始数据
RXBytes = TrafficStats.getTotalRxBytes();
TXBytes = TrafficStats.getTotalTxBytes();
MRXBytes = TrafficStats.getMobileRxBytes();
MTXBytes = TrafficStats.getTotalTxBytes();
RXPackets = TrafficStats.getTotalPackets();
TXPackets = TrafficStats.getTotalPackets();
```

## 4.3.6.3. 监控按钮

按钮触发的实现都放在 `onCreate()` 方法中，并通过调用列表 4.19 所示的 `OnClickListener` 方法引用按钮。在 4.3.12 中定义的权限在监控过程启动时会被检查并接受，以便用户同意监控网络参数所需的权限。这是在按下 `monitorButton` 时执行的，首先触发权限检测，随后启动在 4.3.8 中定义的线程 `mRunnable`，该线程负责参数获取。在指定一秒周期时使用 `m Handler` 来执行。

### 列表 4.19. 监控按钮

```java
// 用于启动监控过程的按钮
monitorButton.setOnClickListener(new View.OnClickListener() {
    @Override
    public void onClick(View v) {
        // 权限访问
        ActivityCompat.requestPermissions(MainActivity.this, new String[]{
            Manifest.permission.INTERNET,
            Manifest.permission.ACCESS_NETWORK_STATE,
            Manifest.permission.READ_EXTERNAL_STORAGE,
            GET_PHONE_STATE;
        }, 100); // 假设此处有请求码，原文未补全

        // 如果尚未接受，则授予权限
        if (Context.checkPermission(MainActivity.this,
            Manifest.permission.INTERNET) != PackageManager.PERMISSION_GRANTED) {
            ActivityCompat.requestPermissions(MainActivity.this, new String[]{
                Manifest.permission.ACCESS_WIFI_STATE,
                Manifest.permission.ACCESS_NETWORK_STATE,
                Manifest.permission.READ_EXTERNAL_STORAGE,
                GET_PHONE_STATE;
            }, 101);
        } else { // 如果 API 不支持流量监控
            if (initRXBytes == TrafficStats.UNSUPPORTED ||
                initTXBytes == TrafficStats.UNSUPPORTED) {
                AlertDialog.Builder alert = new
```

