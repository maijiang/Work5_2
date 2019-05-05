# Work5_2
自定义WebView来加载URL

MainActivity.java
   
    public class MainActivity extends AppCompatActivity {
    private WebView webView;
    private String Url;
    @Override
    protected void onCreate(@Nullable Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
        initView();
        setWebView();
    }

    private void initView() {
        webView= (WebView) findViewById(R.id.webView);
        Uri url=getIntent().getData();
        if(url==null){
            Url="https://www.baidu.com";
        }
        else {
            Url=url.toString();
        }
        Log.e("asd ",Url);
    }
    private void setWebView() {
        WebSettings webSettings=webView.getSettings();
        webSettings.setJavaScriptEnabled(true);
        webSettings.setSupportZoom(true);
        webView.loadUrl(Url);
        webView.setWebViewClient(new WebViewClient(){

            @Override
            public boolean shouldOverrideUrlLoading(WebView view, String url) {
                webView.loadUrl(Url);
                return true;
            }
        });
    }
    }
配置清单文件

     <?xml version="1.0" encoding="utf-8"?>
<manifest xmlns:android="http://schemas.android.com/apk/res/android"
    package="com.example.lenovo.work5_2">


    <uses-permission  android:name="android.permission.INTERNET"/>
    <application
        android:allowBackup="true"
        android:icon="@mipmap/ic_launcher"
        android:label="@string/app_name"
        android:roundIcon="@mipmap/ic_launcher_round"
        android:supportsRtl="true"
        android:theme="@style/AppTheme">
        <activity android:name=".MainActivity">
            <intent-filter>

                <action android:name="android.intent.action.MAIN" />
                <category android:name="android.intent.category.LAUNCHER" />
            </intent-filter>

            <intent-filter>

                <action android:name="android.intent.action.VIEW" />
                <category android:name="android.intent.category.DEFAULT" />
                <category android:name="android.intent.category.BROWSABLE"/>

                <data android:scheme="http"/>
                <data android:scheme="https"/>
            </intent-filter>

        </activity>
    </application>

    </manifest>
    
结果截图：
![Image text](https://raw.githubusercontent.com/hongmaju/light7Local/master/img/productShow/20170518152848.png)
![Image text](https://raw.githubusercontent.com/hongmaju/light7Local/master/img/productShow/20170518152848.png)
