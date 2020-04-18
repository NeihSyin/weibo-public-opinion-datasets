<h1 align="center">weibo-public-opinion-datasets</h1>

<p align="center">Continuously updated Sina Weibo Public Opinion Datasets (only for research use)</p>

<p align="center">
  <a href="https://github.com/nghuyong/weibo-public-opinion-datasets/stargazers">
    <img src="https://img.shields.io/github/stars/nghuyong/weibo-public-opinion-datasets.svg?colorA=orange&colorB=orange&logo=github"
         alt="GitHub stars">
  </a>
  <a href="https://github.com/nghuyong/weibo-public-opinion-datasets/issues">
        <img src="https://img.shields.io/github/issues/nghuyong/weibo-public-opinion-datasets.svg"
             alt="GitHub issues">
  </a>
  <a href="https://github.com/nghuyong/weibo-public-opinion-datasets/">
        <img src="https://img.shields.io/github/last-commit/nghuyong/weibo-public-opinion-datasets.svg">
  </a>
  <a href="https://github.com/nghuyong/weibo-public-opinion-datasets/blob/master/LICENSE">
        <img src="https://img.shields.io/github/license/nghuyong/weibo-public-opinion-datasets"
             alt="GitHub license">
  </a>
</p>

<h2 align="center">Introduction</h2>
Sina Weibo is Chinese largest public social media platform. 
The latest and most popular social events will be disclosed and discussed on Weibo as soon as possible.
Therefore, it is of great significance to build a real-time and full-scale Weibo public opinion dataset.
At present, there are two methods for constructing Weibo public opinion datasets: 

1. Searching public opinion keywords, but due to the limitation of the Weibo search interface, the specified keywords can only obtain up to 1000 data on the specified date.
The overall number of datasets is too low. 
2. Traversing all Weibo users and crawl their tweets containing keywords in a specified period.
However, traversing billions of  Weibo users requires much resources and time!
The overall construction efficiency of datasets is too low.


![](./images/dataset-builder.png)

We propose a new way to construct Weibo public opinion datasets, which can significantly improve the crawling efficiency while maintaining a relatively full amount of data.
Specifically, we dynamically maintain a weibo active user pool, and we will only traverses these users to crawl tweets that include keywords and in a specific period.

Compared with the above method 1, the amount of data for constructing the dataset is greatly increased, 
and especially for popular public opinion keywords, the amount of data is increased by more than **1000 times**.
Compared with the method 2, the data completeness is maintained above **90%**, and the construction efficiency is increased by **20 times**!

<h2 align="center">Weibo Active User Pool</h2>
Based on init seed users and continuous expansion through social relationships, 
we have built a Weibo user pool including more than 300 million users.
The active weibo user pool is constructed based on some filtering rules, and the rules are shown in the following table.

|Item|Rule|Item|Rule|
|:---:|:---:|:---:|:---:|
|Follows number| \> 50 |Tweets number| \> 50 |
|Fans number| \> 50 |Recent post| \< 30 days |

After filtering, the number of Weibo active user pools accounts for about 5% of all Weibo users.

|Download link|Active users|Update time|
|:---:|---:|---:|
|https://pan.baidu.com/s/1EnfGYWro-28eZAsTjlzWXw  Extract Code:eolz|20,000,000|2020-04-19|

## Data Format
```csv
_id,nick_name,gender,province,city,brief_introduction,birthday,tweets_num,follows_num,fans_num,sex_orientation,sentiment,vip_level,authentication,labels,crawl_time
1642909335,微博小秘书,女,北京,,对微博的任何问题请私信@微博客服，或访问客服中心→http://kefu.weibo.com,0001-00-00,4923,2927,199182410,,,6级,微博官方帐号,,1576187979
2671109275,新手指南,女,北京,海淀区,教授新手使用微博方法专业户，每天推荐方法介绍、微博热点...有问题请call我，@、私信都可以，欢迎骚扰~,0001-00-00,17306,2986,185217690,,,7级,新浪微博新手指南官方微博,"新手小技巧,新手大课堂,新手幼儿园",1576148765
2016713117,微博客服,女,北京,海淀区,客服中心→http://kefu.weibo.com；,01-01,14526,155,183843761,,,6级,客服中心首页即可快捷反馈问题；私信咨询请先按照提示选择对应问题分类,"微博帮助,玩转微博,微博客服",1576085666
1934183965,微博管理员,女,北京,,大家好，我的职责是和大家一起维护微博社区秩序。针对微博中的不实信息、抄袭信息、人身攻击等行为请直接投诉，我们会第一时间处理。,1984-10-15,1887,176,159145854,,,6级,新浪微博社区管理官方微博,"举报,求辟谣,不实信息",1575999468
1192329374,谢娜,女,北京,海淀区,太阳女神（也可称为喜神）的光芒照四方呀嘛照四方：）工作邮箱：w761324@qq.com（仅限工作）感谢！,0001-00-00,10183,712,125274267,,,7级,知名女主持人,"社会闲杂人等,主持人",1576189968
1195230310,何炅,男,北京,朝阳区,,0001-00-00,9334,859,118220708,,,7级,湖南卫视知名主持人,主持人,1581017948
2803301701,人民日报,男,北京,,人民日报法人微博。参与、沟通、记录时代。,1948-06-15,112982,3048,113769758,,,6级,《人民日报》法人微博,人民日报,1576189425
5878659096,超话社区,男,北京,,,2016-03-09,5616,1633,113033090,,,6级,超话社区官方微博,北京生活,1576128879
2656274875,央视新闻,男,北京,,“央视新闻”微博是中央电视台新闻中心官方微博，是央视重大新闻、突发事件、重点报道的首发平台。,2012-11-01,124048,2699,107442067,,,6级,中央电视台新闻中心官方微博,,1576059017
1195242865,杨幂,女,北京,,这里有一只狐狸，幸福，感恩，知足，爱~＞＜,0001-09-12,4067,613,107157676,,,7级,演员，代表作《宫》《仙剑奇侠传三》《我是证人》等,"平凡小演员,80后,一只狐狸",1581017987
....
```

[The description of fields](https://github.com/nghuyong/WeiboSpider/blob/master/.github/data_stracture.md#%E7%94%A8%E6%88%B7%E6%95%B0%E6%8D%AE)


<h2 align="center">Weibo Public Opinion Datasets</h2>

|Events|Time Range|Amount|Update time|Other details|
|:---:|:---:|:---:|:---:|:---:|
|Wuhan pneumonia epidemic |2019-11-01 - 2020-03-01| |2020-4-19|[Keyword list]() / [Download link]()|

## Data Format
```csv
_id,comment_num,content,crawl_time,created_at,like_num,repost_num,tool,user_id,weibo_url,image_url,origin_weibo,location_map_info
IuJJEcgnA,10,坐着不舒服嘛  喷什么消毒液 金昌·永昌县 显示地图[组图共2张],1584154051,2020-02-18 09:55,8,4,iPhone客户端,3200312823,https://weibo.com/3200312823/IuJJEcgnA,['http://wx4.sinaimg.cn/wap180/bec0e5f7ly1gc0bc9r1t0j22c0340x6q.jpg'],,"101.977966,38.24474"
IsBZ0xph8,0,【[话筒]#全国累计确诊病例超两万#】截至2月3日24时，国家卫生健康委收到31个省（自治区、直辖市）和新疆生产建设兵团累计报告确诊病例20438例（黑龙江省核减2例），现有重症病例2788例，累计死亡病例425例，累计治愈出院病例632例，现有疑似病例23214例。 转发理由:🙏🙏🙏🙏,1584154050,2020-02-04 10:30,0,0,Android,5680846498,https://weibo.com/5680846498/IsBZ0xph8,['http://wx4.sinaimg.cn/wap180/a716fd45ly1gbk3p61pv1j20j60u4who.jpg'],https://weibo.cn/comment/IsAYNdYB1?rl=1#cmtfrm,
IsoBDk8fn,0,你们能想象吗？经过朋友各方落实，才知道社区根本没有把我们表妹这种危机的状况登记在列，就更谈不上递交街道，让街道递交地区！  社区每次都说“你们要有测试结果才能递交”，然后就没有然后了！谁不想纸张完整的按部就班？！今天说，他们没有收到表妹已经如此严重的信息！ 你们是人吗？？！  医生说，再拖两天可能没治啦，她妈给你们打电话的时候难道会对你们隐藏这样的信息吗？！   要证明自己有这个病真的是太难了啊！！！太难了！！！ 我表妹自从26号CT片出来以后，天天上医院排整体的队，一天睡不满三四个小时，她从中度患者，被药断货、针剂断货，每天疲于奔命的排队问诊，拖到中度，再拖成现在重度病患！ 她们真的是拼劲最后一口气去证明自己患病了啊！她已经气喘不上来，两片肺都感染了也不能证明她症状的严重性吗？！！？ 你们想她们死在奔波的就诊路上，还是死在家，又或是医院，才能证明自己真的是冠状病毒患者？！！！！现在这个情况，大家都很难，我们也知道很难，但是再难，我们没有办法忍心看着28岁的人就这么求天天不应，求地地不灵的死去……  她们母女俩为了排队预约核酸检测和拿药打激素，通宵达旦排队，白天八九点出门，第二天十点多到家。你们能想象无法拿到“正式确诊”的两个新型冠状病毒的母女，妈妈“天天”用轮椅推着已经说不出话的女儿，周转于几家医院。每天没有觉睡，也没有办法保证自己有饭吃，一个可能要断气的人啊，天天为了药、为了打针，为了检测，天天去医院啊！！！！！！谁的免疫力能这么强，这么大强度大体力消耗下还能展示病毒啊？！！？28岁也撑不住啊！！  她们现在连吃饭都成为题，亲戚不在周围，没有交通，你们告诉我，饭都要吃不上了，天天吃鸡蛋，怎么能增强免疫？！没有吃上过一口社区送的饭。小姨天天要给屋子消毒，要带表妹看病，要做饭……… 她现在是轻度感染，这样下去，走的也是表妹的老路！  刚刚小姨说，早上九点半做成了第一次核酸检测，现在要等核酸结果，核酸结果需要48小时，收到第一个核酸检测的结果，24小时之内要找到下一个做核酸的医院，做第二个测试，要两个测试的结果都呈阳性，才能排队等床位……………  是游戏闯关吗？你们做了第一次测试，知道患者是阳性了，你们要做第二次，还要患者去找资源做……… 你们是疯了吗？！再等24小时以后做第二个…… 去哪儿做？做了第一次，就不能给她做第二次吗？上哪儿不是做，为什么要这么安排啊？！  然后现在不断的有朋友告诉我们哪些医院突然可以不用预约做核酸检测，信息不知道是否真实，我们如果能去排的上吗？ 我们真的想多了，我们连车都没有…… 表妹跟她妈妈说，“妈妈，我真的折腾不动了……”  这是要看着她咽气啊……#湖北省集中隔离所有疑似病例##火神山医院交付部队##武汉要求无条件收治所有疑似患者#转发理由:帮转，大家帮帮她吧,1584154050,2020-02-03 00:27,0,0,iPhone客户端,1723298924,https://weibo.com/1723298924/IsoBDk8fn,,https://weibo.cn/comment/IsnMZpYf9?rl=1#cmtfrm,
IrN65rm5y,0,【家属口述｜#一个重症肺炎患者的最后12天#】翁秋秋至死也不知道自己患的是什么病。病势汹汹，从头痛、咳嗽到呼吸困难，“肺全变白了”直至死亡仅仅12天。那是2020年1月21日，新型冠状病毒感染的肺炎疫情正从武汉向全国蔓延，翁秋秋所在的湖北黄冈蕲春县距离武汉不过百余里，黄冈是武汉之外疫情最严重的地区。医生告诉翁秋秋的丈夫陈勇，她患的是不明肺炎。在花光了借来的二十来万医药费后，翁秋秋的病情没有好转，陈勇最终签下放弃治疗的同意书。死亡时，翁秋秋还不满32岁，她刚查出自己怀孕不久。死亡证明上，她的死因写着：“重症肺炎、呼吸衰竭、感染性休克”。全文→http://t.cn/A6PJLJiJ[组图共2张]转发理由:市长以死谢罪都不为过,1584154050,2020-01-30 00:57,0,0,iPhone客户端,1723298924,https://weibo.com/1723298924/IrN65rm5y,['http://wx3.sinaimg.cn/wap180/005vnhZYly1gbclxj7nqaj30go0m8dpu.jpg'],https://weibo.cn/comment/IrCoaxDrx?rl=1#cmtfrm,
IrDd0yOvU,0,⛽️ #抗击新型肺炎我们在行动# #全民口罩行动#  [感冒][感冒][感冒][感冒][感冒] 戴好口罩 勤洗手 多喝水 呆在家里！ ⛽️加油 绿洲 转发理由:啊啊啊啊啊啊啊啊来了来了,1584154055,2020-01-28 23:47,1,0,OPPO R15 梦镜版,5672031187,https://weibo.com/5672031187/IrDd0yOvU,['http://wx2.sinaimg.cn/wap180/005DYQXYgy3gbc4kzguhrj30qo0zkkfc.jpg'],https://weibo.cn/comment/Irysm3bAN?rl=1#cmtfrm,
IqQ9xlZHb,0,#野味肺炎##三部门打击野生动物违法交易# [围观] 每一个生命都值得尊重，不买野生动物制品，别让人类成为最孤单的生命，没有买卖就没有杀害！转发承诺！ [组图共9张]转发理由:转发微博,1584154050,2020-01-23 18:54,0,0,iPhone客户端,1723298924,https://weibo.com/1723298924/IqQ9xlZHb,['http://wx3.sinaimg.cn/wap180/007HSmylly1gb5n4t9twuj30dw0dwta7.jpg'],https://weibo.cn/comment/IqHzUmOFz?rl=1#cmtfrm,
IskDtcJ1J,0,Sp.005【 关于新冠肺炎的一切 】  这场突然爆发的新型冠状病毒肺炎是如何发生和传播的？死亡率和传播速度有多高？如何降低被感染的可能性？在这支视频中，我们会试图回答你我关心的一切问题。  *关注我们的微博，在私信回复「肺炎」，可获取本期视频的文字稿和引用资料。 回形针PaperClip的微博视频 转发理由:一定能过去……,1584153758,2020-02-02 14:20,0,0,小米Max3 大屏大电量,7101981194,https://weibo.com/7101981194/IskDtcJ1J,,https://weibo.cn/comment/IsizhBjTy?rl=1#cmtfrm,
IwkiNE93a,0,已经复工和即将复工的大家，#2019冠状病毒病# 疫情还没有结束，千万不要掉以轻心@联合国环境规划署 @世界卫生组织 @微公益 [组图共6张]转发理由:好的哥哥,1584153297,2020-02-28 20:51,0,0,HUAWEI P30 Pro,6570734069,https://weibo.com/6570734069/IwkiNE93a,['http://wx1.sinaimg.cn/wap180/9b884b3bly1gc9x5tqlclj20l00l00u7.jpg'],https://weibo.cn/comment/Iw03ZDWXG?rl=1#cmtfrm,
IrkkiszBX,0,这波禁止吃野味的标语太强了，还挺押韵，建议每个人全文背诵  #广东新增新型肺炎13例# [组图共9张]转发理由:轉發微博,1584154031,2020-01-26 23:43,0,0,iPhone客户端,5217981766,https://weibo.com/5217981766/IrkkiszBX,['http://wx2.sinaimg.cn/wap180/006U7FRcly1gba62t2p5uj30qo0peace.jpg'],https://weibo.cn/comment/Irivy2rCh?rl=1#cmtfrm,
IrfR39ofD,0,#延长假期##钟南山说动才动#希望延长啊  特别北上广深 人流量密集的城市，每天地铁挤得水泄不通，很痛连锁感染。 面对疫情，你希望单位延长假期吗?,1584154031,2020-01-26 12:20,1,0,iPhone客户端,5217981766,https://weibo.com/5217981766/IrfR39ofD,,,
...
```

[The description of fields](https://github.com/nghuyong/WeiboSpider/blob/master/.github/data_stracture.md#%E5%BE%AE%E5%8D%9A%E6%95%B0%E6%8D%AE)


<h2 align="center">Citation</h2>
If you use this work in a scientific publication, I would appreciate references to the following BibTex entry:

```
@misc{nghuyong2020@weibo-public-opinion-dataset,
  title={weibo-public-opinion-dataset},
  author={Yong Hu},
  howpublished={\url{https://github.com/nghuyong/weibo-public-opinion-dataset}},
  year={2020}
}
```