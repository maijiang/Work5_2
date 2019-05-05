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
