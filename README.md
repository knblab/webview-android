# Website-to-Android-WebView Converter (webview-android)
Converting a website to an Android WebView app can be done using the following steps:

## Getting Started
1. Clone this repository to your local machine.
2. Open the project in Android Studio.
3. Add a WebView component to your project's layout file. You can do this by adding the following code to your XML layout file:

```
<WebView
        android:id="@+id/browser"
        android:layout_width="match_parent"
        android:layout_height="match_parent" />
```


4. In your main activity, Declare and initialize the WebView and load the URL of the website you want to convert.

```
public class MainActivity extends AppCompatActivity {
    WebView webView;
    
    ....
```

Add the following code to your main activity's `onCreate()` method:
```   
      webView =  findViewById(R.id.browser);
      webView.setWebViewClient(new WebViewClient());
      webView.loadUrl("https://www.hespress.com");
      WebSettings webSettings = webView.getSettings();
      webSettings.setJavaScriptEnabled(true);
```


Add the following code to your main activity's `Class` outside `onCreate()` method:
```
 @Override
public void onBackPressed() {
        if(webView.isFocused() && webView.canGoBack())
        {
            webView.goBack();
        }else{
            super.onBackPressed();
        }
}

private class MywebClient extends WebViewClient{
        @Override
        public void onPageStarted(WebView view, String url, Bitmap favicon) {
            super.onPageStarted(view, url, favicon);
        }
        @Override
        public boolean shouldOverrideUrlLoading(WebView view, WebResourceRequest request) {
            return super.shouldOverrideUrlLoading(view, request);
        }
}

   
```


5. Add Internet permission to the `AndroidManifest.xml` file. You can do this by adding the following code to the manifest file:

```
<uses-permission android:name="android.permission.INTERNET" />
```

6. Customize your app's settings, such as the app icon, name, and theme, as desired.
7. Build and run your app.
