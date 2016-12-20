# jsoup
jsoup简介，jsoup实现带cookie的连接

1. 使用 jsoup 对 HTML 文档进行解析和操作
https://www.ibm.com/developerworks/cn/java/j-lo-jsouphtml/

2. Jsoup模拟登陆例子
http://qindongliang.iteye.com/blog/2086102

3. Jsoup结合WebDriver进行带coolie的连接，获取网页内容

Set<Cookie> cookies = driver.manage().getCookies();
Map<String, String> coolies_map = new HashMap<String, String>();
  for (Cookie cookie : cookies) {
    coolies_map.put(cookie.getName(), cookie.getValue()); 
}

// org.jsoup.Connection
Connection conn = Jsoup.connect(url);
conn.header(""User-Agent", "Mozilla/5.0 (Windows NT 6.1; WOW64; rv:29.0) Gecko/20100101 Firefox/29.0"");
... ...

conn.cookies(coolies_map);
Document doc = conn.post();

官网文档：

https://jsoup.org/apidocs/org/jsoup/select/Selector.html
https://jsoup.org/cookbook/extracting-data/selector-syntax
https://jsoup.org/cookbook/extracting-data/attributes-text-html
https://jsoup.org/cookbook/extracting-data/example-list-links
