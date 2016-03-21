# CordovaHostWebApp
> Cordova App讀取遠端Web App做為App的頁面內容

1. config.xml -> 檢視程式碼.
2. 在< platform >區段前加入以下設定 (http://codeian.idv.tw/ 改為你的Web App網址)

		<allow-navigation href="http://codeian.idv.tw/" />

3. index.html < meta http-equiv="Content-Security-Policy"... > 使用以下程式碼取代 (http://codeian.idv.tw/ 改為你的Web App網址)

 		<meta http-equiv="Content-Security-Policy" content="default-src 'self' 
		data: gap: http://codeian.idv.tw/ https://ssl.gstatic.com 'unsafe-eval'; 
		style-src 'self' 'unsafe-inline'; media-src *">


4. index.js -> onDeviceReady()事件在撰寫以下程式碼

		function onDeviceReady() {
	        // 處理 Cordova 暫停與繼續事件
	        document.addEventListener( 'pause', onPause.bind( this ), false );
	        document.addEventListener( 'resume', onResume.bind( this ), false );
	        
	        // TODO: Cordova 已載入。請在這裡執行任何需要 Cordova 的初始化作業。
	        
	
	        // Here, we redirect to the web site.
	        var targetUrl = "http://codeian.idv.tw/";
	        window.location.replace(targetUrl);
    	};

