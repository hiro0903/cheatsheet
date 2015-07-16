# Web API - 使用者影音串流輸入

1. 參考資料: https://developer.mozilla.org/en-US/docs/Web/API/MediaDevices/getUserMedia
2. 目前瀏覽器都需要prefix
3. 透過navigator.getUserMedia 取得符合條件的裝置列表 

    ```js
    var mediaList = new Promise(function(res, rej) { //使用promise方式處理相對簡單, 但也可以自行提供onSuccess跟onFail的callback

        navigator.webkitGetUserMedia({ //目前還在experimental階段, 需要prefix
        
                audio : true,   //@param {object} constraints - 要取得的媒體型別
                
                video : false   //如果只有麥克風的情況, video false 或者 沒寫 可以取得, video true會找不到
                                //另外也可以video : { width: 800, height: 600 }, 更多規格可看mdn連結
                                
            }, 
            res, //參數2 為 onSuccess, callback param: {MediaStream}
            rej  //參數3 為 onFail,    callback param: {MediaStreamError} - 兩種可能: 權限不足或找不到符合的裝置
        );
    });
    ```
4. 取得MediaStream後, 如果要做為video or audio的src, 需要透過 window.URL.createObjectURL

    ```js
    
    var video = document.createElement('video');
    video.src = window.URL.createObjectURL( stream ); //{MediaStream} stream
    video.onloadedmetadata = function(e) {
        video.play();
    }; 
    
    ```
5. 待補
