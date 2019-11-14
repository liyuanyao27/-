# 标点处理
## 对没有标点长恨歌加标点插并入在控制台查询某字出现次数    
### 中文字符判断方法  

`public static boolean isChineseChar(String string) {	 `  
`       Pattern p = Pattern.compile("[\u4e00-\u9fa5]");`  
`       Matcher m = p.matcher(string); `  
`        if (m.find()) { `  
`            return true; }`    
 `       return false;}  `  
 
 上面这个方法是我自定义的，用了正则表达式的方法匹配字符串。关于 ***"[\u4e00-\u9fa5]"*** 这个东西，是中文unicode编码，并且正好是中文编码的开始和结束的两个值，用这个匹配我的字符串是不是中文字符是非常方便的。
 
 接下来就是主程序了，根据要求必然是用数组传参。   
 `public static void main(String args[])`  
 因为不需要图形化显示，所以我就直接在控制台进行输入输出了。  
 我运用了异常处理的方法，如果不是中文字符的话会抛出异常，然后再 ***catch*** 异常，对异常进行处理，处理的方法是跳过这次循环继续下一次循环，如果是中文的字符的话就跳出异常显示字符出现的次数。出现的字数也用了正则表达式的类***Patern***，当然这个程序用不到正则表达式，与match创建一个匹配搜索模式而已。
 这部分有点多，详情在程序的第53行里，我就挑重点展示一下。  
`        Pattern p = Pattern.compile(d);//创建正则表达式`  
`        Matcher m = p.matcher(s1);//创建合适的匹配器`  
`        while(m.find()) {//匹配函数，true时执行`  
`        n1++;//数值加1}`
 
 ### 对于长恨歌的分句  
 这涉及到如何去分句呢？Java不像python那么简单，直接遍历然后放进列表操作就可以。我们可以采取循环的方式，在第七个字后应该加逗号，在第14个字后加句号
 String提供了一个方法 ***insert(int，char)*** 即在字符串的第参数位加入你想加的字符。以下是我的程序  
 
`        int last = s1.length();`  
`        int a= last/7+last/14;`  
`        for(int i = 14; i < last+a; i+=14) {`  
`	s1.insert(i-7,',');`  
`        i++;`  
`        s1.insert(i,'\n');`  
`        s1.insert(i,'.');`  
`        i+=2;}`  

我们要先进行对字符串字数的统计，然后计算要添加进的字符数量，别忘了除了冒号和逗号还有'/n'，所以每句有三个字符。把总数last+a作为循环限制，隔14个字符循环一次，在往前-7位就是加逗号的地方，i++是因为添加了一个逗号就多了一位，所以重新计数，加句号的地方就是原来的地方加一位，而加句号的地方就是I+=2,因为有/n和句号的存在。  
最后输出就大功告成啦！
### 输出结果  
汉皇重色思倾国,御宇多年求不得.  
杨家有女初长成,养在深闺人未识.  
天生丽质难自弃,一朝选在君王侧.  
回眸一笑百媚生,六宫粉黛无颜色.  
春寒赐浴华清池,温泉水滑洗凝脂.  
侍儿扶起娇无力,始是新承恩泽时.  
云鬓花颜金步摇,芙蓉帐暖度春宵.  
春宵苦短日高起,从此君王不早朝.  
承欢侍宴无闲暇,春从春游夜专夜.  
后宫佳丽三千人,三千宠爱在一身.  
金屋妆成娇侍夜,玉楼宴罢醉和春.  
姊妹弟兄皆列士,可怜光采生门户.  
遂令天下父母心,不重生男重生女.  
骊宫高处入青云,仙乐风飘处处闻.  
缓歌慢舞凝丝竹,尽日君王看不足.  
渔阳鼙鼓动地来,惊破霓裳羽衣曲.  
九重城阙烟尘生,千乘万骑西南行.  

请输入想要查询的字符(串)：  
三千  
该字符(串)在文本中出现了2次
