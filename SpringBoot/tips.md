# interceptorとfilter
* https://meetup-jp.toast.com/698
* interceptorとfilterとAOPはどれも処理を挟めるタイミングがちがう、この3つを使えるようにればどのタイミングでも処理を挟めるようになる
FilterはServletで処理の前後を扱うことができる。 
* InterceptorはHandlerの実行前（preHandle）、Handler実行後（postHandle）、viewレンダリング後（afterCompletion）など、Servlet内でもメソッドに基づいて実行時点が異なる。
<br>AOPはクラスの処理(メソッド)の前後