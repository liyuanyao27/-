# -
对没有标点长恨歌加标点插入在控制台查询某字出现次数
###中文字符判断函数
`<public static boolean isChineseChar(String string) {	
        Pattern p = Pattern.compile("[\u4e00-\u9fa5]");
        Matcher m = p.matcher(string);
        if (m.find()) {
            return true;
        }
        return false;}  >`
