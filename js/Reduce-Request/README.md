## 說明 ##

在我們的專案中，有專門提供訊息文字的Web api，當User的操作符合否些特定規則時(例如使用者輸入錯誤資訊)，會用ajax向api要訊息並顯示於畫面中。

有時候，訊息往往為非敏感性且不常變動的值，每次的Request彷彿是毫無意義的重複撈取相同的結果，增加系統的運行成本，拖慢系統使用速度(假如又遇到連續觸發Request的場合，真是一場災難)；此時，我們所期望的是只有**第一次**真正發送Request並將結果儲存起來，爾後只取用記憶體中的結果。

該範例將使用JS closure的特性及簡單的 Design Pattern 實作出理想結果。
	
	
    var getMessage = function(){
		var _result=null;

		//取得ajax回傳的結果
		_result = getAjaxResult();

		// 重寫方法，回傳_result(取代原本會觸發ajax的function內容)
		getMessage=function(){
			return _result;
		}
		
		//直接呼叫取得_result
		return getMessage();
	}
<br>

	//call function
	getMessage(); //第一次觸發Request
	getMessage(); //不會觸發Request
	getMessage();



<a href="http://jsbin.com/duwobaq" target="_blank">Demo</a>