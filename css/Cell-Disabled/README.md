## 說明 ##
當我們期望Table中所有的輸入框都是 disabled，如下圖：

![alt tag](https://raw.githubusercontent.com/LezardYeh/Front-end/master/css/Cell-Disabled/img.jpg)

直覺上會用JS去取得DOM，依序把所有input加入disabled屬性，這作法雖然單純卻耗用相當大的成本；
若以CSS來處理，我們將省去用JS再次與DOM互動的過程，直接達到相同效果。
其實作概念為：

1. 運用 ::after 讓TD內容中產生偽元素；
1. 定義偽元素的position及其他style；
1. 讓它覆蓋在TD內容中，使User無法點擊TD中的Input Box。

<a href="https://htmlpreview.github.io/?https://github.com/LezardYeh/Front-end/blob/master/css/Cell-Disabled/index.html" target="_blank">Demo</a>
> 注意：position:absolute使用時，要定義上層物件的position，否則位置會錯誤。