## 数据说明
* raw下poems.txt是收集从唐到清的绝句和律诗，sentences.txt是以句号分句形成的句对
* manually下包含人工标注和收集的比喻、拟人、夸张句对数据
* automatically下包含有词句规则提取的比喻、拟人、夸张句对数据

原始的数据，唐诗三百首可从http://www.shiku.org/shiku/gs/tangdai.htm 获取，比较全的中文诗歌数据可从https://github.com/yaonphy/PoetryLibrary 中获取

## 词句规则
每类修辞都有一些明显的关键词或语言模式，比如如果诗句中出现 ”如(似)雪(烟画丝) 月似钩 月作钩“ 等关键词就可以认为是比喻，这些特征可以写成规则用正则表达式来提取，正则表达式如下：
*  比喻
`
reg = "(化为|化作|仿佛|恰似|犹似|宛是|宛若|宛如|应似|月似钩|月作钩|青如淀|青如粟|似锦|[如似].*(雪|烟|画|丝|花|落花|草|叶|落叶|柳|杨柳|竹|梅|松|荷|梧桐|梧|莲|牡丹|兰|蝉|鸿鹄|凤凰|凰|凤|殴|鹰|子规|燕|鱼|鹤|蝶|燕|雁|鹊|鹭|鹃|莺|月|霜|海|雨|秋|风|春|春风|秋风|云|雪|水|冰|雷|面|云稼|麻|仙|玉|泪|颜|毛|弓|簪|鲸|羽|箭|诗|霓|酥|发|虹|愁|锦|练|萍|雹|河|星|苇))"
`
* 拟人
`
reg = "(送春归|怨柳|怨杨柳|春风知|花溅泪|[争斗][艳妍]|斗芳菲|笑春风|花[泣泪]|白云愁色|江山不管|潜入夜|山月不知|青鸟不传|淡妆浓抹|羌笛何须|(花|落花|草|叶|落叶|柳|杨柳|竹|树|梅|松|荷|梧桐|梧|豆|莲|牡丹|苔|兰|蝉|鸿鹄|凤凰|凰|凤|殴|马|鹰|子规|鸟|燕|鱼|鹤|蝶|燕|雁|鹊|鹭|鹃|莺|猿|月|霜|海|雨|山|秋|风|春|春风|秋风|云|雪|水).*(有意|无意|迎春|送春|送秋|有心|有梦|无心|有情|无情|送行舟|不管|愁色|春意闹|寂寞|思|恋|哭|泪|恨|怨|泣|牵别恨|无力))"
`
* 夸张
`
reg = "(无垠|石烂|海枯|抵万金|满城|星垂|天际流|踪灭|断绝|海天愁思|[千万]行泪|白云间|万仞山|无数|[千万][壑年重尺丈顷]|断肠|横绝|万重云|[上下去入到落](银河|青天|青云|九天|九霄|云霄)|吞[海天云日月山]|[揽摘扪](月|明月|星|日)|行[千万]里|万里心|泣鬼|惊(鬼神|天地|风雨)|化为龙|化龙|天上来|上天去|波撼|高[千万]|吸百川|倾城|轻鸿毛|重泰山|飞绝)"
`

Note：规则提取的方式会引入一些噪声，可以在此基础上做二次筛选
