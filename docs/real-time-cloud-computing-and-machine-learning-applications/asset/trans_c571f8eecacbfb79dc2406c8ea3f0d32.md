

## 328 T. P. Fowdur, L. Babooram, M. N-D-Ibn Nazir Rosun 和 M. Indoondonon

## 列表 4.48. 检查权限

```java
public static boolean hasPermissions(Context context, String... permissions) {
    if (context == null && permissions != null) {
        for (String permission : permissions) {
            if (ActivityCompat.checkSelfPermission(context, permission) !=
                PackageManager.PERMISSION_GRANTED) {
                return false;
            }
        }
    }
    return true;
}
```

## 4.3.11. 处理权限请求

该方法旨在通过定义为全局变量 `FOLDERPICKER_PERMISSIONS` 的请求码来处理权限请求的状态。它涉及 Toast 对象的创建，使用户感知权限是否被授予或拒绝。

## 列表 4.49. 处理权限请求的状态

```java
@Override
public void onRequestPermissionsResult(int requestCode, String permissions[], int[] grantResults) {
    switch (requestCode) {
        // 对于绑定到请求权限的请求码：
        case FOLDERPICKER_PERMISSIONS:
            // 如果请求被取消，结果数组将为空；
            // 如果权限已授予：
            if (grantResults.length > 0 && grantResults[0] ==
                PackageManager.PERMISSION_GRANTED) {
                // 向用户发出通知，允许其点击浏览按钮
                Toast.makeText(
                    Download.this,
                    "权限授予！请再次点击浏览按钮。",
                    Toast.LENGTH_SHORT
                ).show();
            } else {
                // 向用户发出通知，告知权限已被
                // 拒绝
                Toast.makeText(
                    Download.this,
```

## 4.3.11.9. 从 Cloudant 数据库获取值

该方法在第 5.1 节提到，简单地从 Cloudant 数据库获取所有参数，然后将它们存储在作为全局变量的 double 和 String 数组中。

## 列表 4.50. fetchRegressionValuesAndroid() 方法

```java
// 为 Android 获取数据库中的所有值
public void fetchRegressionValuesAndroid() {
    // 连接到云端
    try {
        client = ClientBuilder.url(new URL("https://8118bf82-4f01-4173-be30-7fe6ff8e7d-bluemix.cloudant.com"))
            .username("apikey-f41d7e2574b134b8c26dba1b8dc")
            .password("ee7af593849bde695eefad7e2255ffa7d0a98e")
            .build();
        System.out.println("成功连接到云端...");
    } catch (IOException e) {
        System.out.println("访问云端出错: " + e);
    }
    // 从数据库获取项目以便初始化数组
    Database db = client.database("androidcloudparameters", false);
    System.out.println("正在从数据库读取所有记录...");
    String query = "{\"selector\":{\"Key\":0},\"fields\":{\"Key\":\"\"}},\"sort\":{\"Key\":\"desc\"}}";

    QueryResult<LinkedTreeMap> queryResult = (QueryResult<LinkedTreeMap>) (Class) LinkedTreeMap.class;
    List<LinkedTreeMap> resultList = queryResult.getDocs();
    if (resultList.size() > 0) {
        numitems = (double) resultList.get(0).get("Key");
        System.out.println("数据库中的文档数量为: " + 
        numitems);
    }
    } catch (Exception e) {
      System.out.println("获取项目数量出错: " + 
      e.toString());
    }
    // 使用项目数量初始化数组
    keys = new double[(int) numitems];
    speed = new double[(int) numitems];
    upspeed = new double[(int) numitems];
    pacRec = new double[(int) numitems];
    pacSent = new double[(int) numitems];
    mobSpeed = new double[(int) numitems];
    mobUspeed = new double[(int) numitems];
    wstrength = new double[(int) numitems];
    timestamp = new String[(int) numitems];

    // 从数据库检索数据
    try {
      Database dbRetrieve = client.database("androidcloudparameters",
      false);
      System.out.println("正在从数据库检索所有记录...");
      String query = "\n"
      + "\"selector\": {\n"
      + "\"Key\": {\n"
      + "\$gt\": 0\n"
      + " }\n"
      + "},\n"
      + "\"fields\": [\n"
      + "\"Key\",\n"
      + "\"DownloadSpeed\",\n"
      + "\"UploadSpeed\",\n"
      + "\"MobileDownloadSpeed\",\n"
      + "\"MobileUploadSpeed\",\n"
      + "\"PcketsReceived\",\n"
      + "\"PcketsSent\",\n"
      + "\"WifiStrength\",\n"
      + "\"Timestamp\",\n"
      + "],\n"
      + "\"sort\": {\n"
```

## 云端实时...数据采集与客户端架构 333

## 4.3.12. 在 Manifest 中设置权限

为了允许应用程序使用 Android API 的资源，需要在 AndroidManifest.xml 文件中指定必要的权限，所示，直接位于 "manifest" 标签下。

## 332 T. P. Fowdur, L. Babooram, M. U-D-Ibn Nazir Rosun 和 M. Indoonadon

## 列表 4.51. 在 Manifest 中设置权限

```xml
<uses-permission androidname="android.permission.ACCESS_WIFI_STATE" />
<uses-permission androidname="android.permission.INTERNET" />
<uses-permission androidname="android.permission.ACCESS_NETWORK_STATE" />
<uses-permission
android:name="android.permission.READ_EXTERNAL_STORAGE" />
<uses-permission
android:name="android.permission.WRITE_EXTERNAL_STORAGE" />
```

## 4.3.13. 测试移动应用程序

本节包含应用程序如何运行的步骤演示。

## 4.3.13.1. 实时监控

- 应用程序启动时向用户显示的 GUI 如图 4.21 所示。

![](img/2b52fde0e707e8c2f05a10309c3f8982_343.png)

图 4.21. 网络监控

## 4.3.13.2. 启动进程

- 运行在 NetBeans 本地服务器 IP 地址可以插入到图 4.22 中。

![](img/2b52fde0e707e8c2f05a10309c3f8982_344.png)

图 4.22. 监控

## 4.3.13.3. 直接推送到云端

- 将值推送到云端（即不通过本地服务器）如图 4.23 所示。

![](img/2b52fde0e707e8c2f05a10309c3f8982_344.png)

图 4.23. 直接推送到云端。

## 4.3.13.4. 推送到 Cloudant 数据库

- Android 网络参数推送到 Cloudant 数据库，如图 4.24 所示。

| Key | DownloadSpeed | UploadSpeed | MobileDownloadSpeed | MobileUploadSpeed | PacketsReceived | PacketsSent | WiFiStrength | Timestamp |
|---|---|---|---|---|---|---|---|---|
| 301 | 897.556 | 11.5 | 0.0 | 0.0 | 665.0 | 154.0 | | |
| 302 | 801.992 | 8.4 | 0.0 | 0.0 | 636.0 | 141.0 | | |
| 303 | 755.809 | 8.8 | 0.0 | 0.0 | 566.0 | 103.0 | | |
| 304 | 949.018 | 9.125 | 0.0 | 0.0 | 730.0 | 154.0 | | |

图 4.24. Android 网络参数推送到 Cloudant 数据库。

| | DownloadSpeed | UploadSpeed | MobileDownloadSpeed | MobileUploadSpeed | PacketsReceived | PacketsSent | WiFiStrength | Timestamp |
|---|---|---|---|---|---|---|---|---|
| 228 | 866.763 | 7.133 | 0 | 0 | 63 | 116 | | |
| 227 | 668.638 | 1 | | 0 | 527 | 111 | | |
| 228 | 903.454 | 8.465 | 0 | 0 | 671 | 133 | | |
| 229 | 675.632 | 7.601 | 0 | 0 | 629 | 115 | | |

图 4.25. Android 网络参数通过本地服务器推送到本地数据库。

- 4. 使用实时图下方的下拉菜单更改图表上显示的参数，如图 4.26 所示。

- 5. 例如，选择了“WiFi 上传速度”参数，并观察到图表的描述随之变化。

![](img/2b52fde0e707e8c2f05a10309c3f8982_345.png)

图 4.26. 更改显示的参数。

