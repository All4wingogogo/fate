# 命运：现代科学取名工具 #
# FATE: A modern science chinese name create tool #
## Github第一个开源的中文取名项目 ##
## The first chinese name create tool in github ##

## [起名算法中目前排第一个](https://www.google.com/search?q=%E8%B5%B7%E5%90%8D%E7%AE%97%E6%B3%95&oq=%E8%B5%B7%E5%90%8D%E7%AE%97%E6%B3%95&aqs=chrome..69i57.3721j0j8&sourceid=chrome&ie=UTF-8) ##

### 一个好名字伴随人的一生，FATE让你取一个好名字 ###
程序适用于单个姓或双个姓，起2个名的情况。（如：独孤**，李张**，张**，王**）  

### 参考算法 ###
  周易卦象  
  大衍之数  
  三才五格  
  喜用神（平衡用神）  
  生肖用字  
  八字吉凶  

#### 版本履历:

第一版:
    大部分是手动工作,现已废弃
    
第二版:
    可自动生成名字字符 + 手工筛选
    
第三版(开发中):
    每次生成一个名字,并目标喜用神,生肖喜忌,月历转换,生成八字等功能  
    八字计算: https://github.com/godcong/chronos  
    字典数据: https://github.com/godcong/excavator  
    数据库重新切回mysql,mongo虽然插入简单,检索语法太繁琐了...
    
    起名算法:
    算法(进度) 备注
    五格(95%) 暂用字库已补全
    三才(95%) 暂用字库已补全
    八字(100%) 喜用神完成, 补八字完成
    卦象(100%) 算法完成，起卦完成,吉凶过滤完成。
    生肖(30%) 生肖获取完成,字库筛选待完成
    天运(TODO)
    
第四版(计划):  
    通过AI,大数据匹配算法,取出更好更佳的名字.


写在最后,接口Readme:
```   
        使用前请导入pre的数据（测试字库尚未完善，生成姓名后可以去一些测名网站验证下）
        //连接mysql数据库
    	eng := fate.InitMysql("192.168.1.161:3306", "root", "111111")
        //生日
    	c := chronos.New("2020/01/23 11:31")
        //姓名的最少笔画数（可不设）
    	fate.DefaultStrokeMin = 3
        //姓名的最大笔画数（可不设）
    	fate.DefaultStrokeMax = 15
 
        //设定数据库：fate.Database(eng)
        //开启八卦过滤：fate.BaGuaFilter()
        //开启生肖过滤：fate.ZodiacFilter()
        //开启喜用神过滤：fate.SupplyFilter()
        //第一参数：姓
        //第二参数：生日 
    	f := fate.NewFate("王", c.Solar().Time(), fate.Database(eng), fate.BaGuaFilter(), fate.ZodiacFilter(), fate.SupplyFilter())
    
    	e := f.MakeName(context.Background())
    	if e != nil {
    		t.Fatal(e)
    	}
```


### 其他(补充资料) ###

立春：  
2019年02月04日 11:14:14  
2020年02月04日 17:03:12  
2021年02月03日 22:58:39  
2022年02月04日 04:50:36  
2023年02月04日 10:42:21  
2024年02月04日 16:26:53  
2025年02月03日 22:10:13  
生肖按八字算从立春开始算起，不到时间则为上一年。

1、配合八字命理的喜忌，是起名字的核心所在。     
八字是每个人出生的年、月、日、时，小孩取名的第一步即是分析八字，了解命理五行所缺并找出喜用神，并且据此起名，这是最关键的核心，所有姓名的吉凶预测与取名，都以此为准。     
2、名字用字字义务必吉祥     
中国文字的魅力在于，每个方块字不仅都有其本身的含义，而且还有其特殊的周易诱导含义，名字在很多时候它还会影响到人性格的形成，正所谓“名如其人”。
所以一个好的名字，务必用字字义吉祥。
宝宝起名字确实需要考虑很多因素，不仅要考虑读音、字形以及各种禁忌更重要的是要考虑宝宝的生辰八字，因此给孩子起名还是找专家比较好。
现在这方面比较知名的应该是温雅居士了，温雅居士在宝宝起名方面有着十几年的经验独创易学起名法：排八字、看五行、测五格、配三才、合属相、想寓意、听音律、写字形，在业界目前应该是比较权威的了。
取名是需要非常系统考虑的，不能只考虑读音一个方面，温雅居士采用的排八字、看五行、测五格、配三才、想寓意、听音律、写字形的综合起名法非常喜欢。     
3、五格数理，特别是主格的数理要为吉数。     
在姓名学中，数理产生许多福祸吉凶的灵动力，对人生影响很大。
这跟单个姓名用字的笔划好坏无关，准确的福祸吉凶是按照特殊方式计算数理的。     
4、三才配置一定不可以相克。     
三才配置在姓名学中，占有很大的分量。三才配置指的是天格、人格、地格之间的关系。中国传统文化中有顺应天时、地利、人和的行事哲理；
测名过程中，有很多姓名数理不错，但是三才配置不佳，大多表现为运气反复，遇事受阻碍，且感情及财运不好。
三才配置相生相克的关系定吉凶，同样也影响着一个人事业成功率的高低。     
5、五格配置在姓名学中占有主要位置。     
五格配置是指天格、地格、人格、外格、总格共五格之间的关系。
天格是由祖先流传而来，单独出现对人生没有多大影响；人格是姓名剖象数理的中心所在，对人生的影响最大；
人格与地格结合的数理则为基础运。地格主要是36岁前的人生，也叫前运力，外格代表人的外围，吉凶无谓。总格是36岁以后的人生，也是后运力。     
6、小孩取名字时还要结合命主的出生方位、父母资料等因素，以达到事半功倍的效果。  
  其实任何事情道理都是一样的，只有适合自己的才是最好的。

周易卦象编码参考:

六十四卦
# ䷀ ䷁ ䷂ ䷃ ䷄ ䷅ ䷆ ䷇ ䷈ ䷉ ䷊ ䷋ ䷌ ䷍ ䷎ ䷏ 
# ䷐ ䷑ ䷒ ䷓ ䷔ ䷕ ䷖ ䷗ ䷘ ䷙ ䷚ ䷛ ䷜ ䷝ ䷞ ䷟ 
# ䷠ ䷡ ䷢ ䷣ ䷤ ䷥ ䷦ ䷧ ䷨ ䷩ ䷪ ䷫ ䷬ ䷭ ䷮ ䷯ 
# ䷰ ䷱ ䷲ ䷳ ䷴ ䷵ ䷶ ䷷ ䷸ ䷹ ䷺ ䷻ ䷼ ䷽ ䷾ ䷿ 

八卦
# ☰ ☱ ☲ ☳ ☴ ☵ ☶ ☷

四象
# ⚌ ⚍ ⚎ ⚏

两仪
# ⚋⚊

为什么要集六大派与一体?  
看下下面这个统计,每一派的取名法其实都有其不足之处.  
• 笔划派：	认为笔划全吉，人生就大吉。其实准确度仅12.5 %   
• 三才派：	完全不管笔划吉凶，只认为天地人三才五行相生，人生就大吉。其实准确度仅56.6 %。  
• 补八字：	完全不管笔划吉凶，只认为名字补到先天八字命盘欠缺，人生就大吉。其实准确度非常低。  
• 卦象派：	完全不管笔划吉凶，只认为名字求出卦象漂亮，人生就大吉。其实准确度仅40.26 %。  
• 天运派：	完全不管笔划吉凶，只认为名字不要被出生年天运五行所剋，人生就大吉。其实准确度仅25.32 %。  
• 生肖派：	完全不管笔划吉凶，只认为生肖用对字形，人生就大吉。其实准确度仅27.55 %。  

PS:最近看到有人别出心裁说三才不准,并举了一些名人的例子.  
然后他倒过来算,发现很符合,很正确.  
那我也就呵呵了,按准确度来算,非正即反.  
你倒过来算,不准的变准了.那原来准的那些不就不准了.  
在我看来事分阴阳,而这接近一半的准确度则恰到其好处.  

所以,遵照传统为自己的宝宝起一个中正平和的名字才是最好的.  
从概率论的角度来讲,相交得到的最终结果.其准确度最高.  
所以,单纯得拿一种或两种方法来取名是不可取的.  
尽量符合多种的名字才是最佳,但并不一定需要全中.  
Fate的本意是让起名变得简单,且能取到一个好的名字.  
有人会花个十几,几十万取一个名字(周围的真人真事),  
但是这个名字好不好你却未必知道.  
算法开源就是为了让每个人知道,  
这个名字取名过程的来龙去脉.  

