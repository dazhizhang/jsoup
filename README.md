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
conn.header("Connection", "keep-alive");
try {
  URL _url = new URL(url);
  conn.header("Host", _url.getHost());
} catch (MalformedURLException e) {
  throw Lang.wrapThrow(e);
}
conn.header("User-Agent", "Mozilla/5.0 (Windows NT 6.3; WOW64; rv:39.0) Gecko/20100101 Firefox/39.0");
conn.header("Accept", "text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8");
conn.header("Accept-Language", "en-US,zh-CN;q=0.8,zh;q=0.5,en;q=0.3");
conn.header("Accept-Encoding", "gzip, deflate");
conn.header("Cache-Control", "max-age=0");
conn.timeout(WaitTime.Longer.valInMS());

conn.cookies(coolies_map);
Document doc = conn.post();
