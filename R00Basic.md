# R00Basic
Jilung Hsieh  
2018/3/6  



* Slide: https://docs.google.com/presentation/d/e/2PACX-1vRjb_W1Vo9-zD9F4FmWOiB6K4ezkF6W64OKcX7bZD6ordKvOT-6LFoGi0le-HzT2ABKudDNhr_qKt2x/pub?start=false&loop=false&delayms=3000&slide=id.g2074c710b4_0_293

# Installing and loading packages

```r
# install.packages("tidyverse")
```

# Reading data


```r
load(url("http://varianceexplained.org/files/trump_tweets_df.rda"))
head(trump_tweets_df, 3)
```

```
## Warning in as.POSIXlt.POSIXct(x, tz): unknown timezone 'zone/tz/2018c.1.0/
## zoneinfo/Asia/Taipei'
```

```
##                                                                                                                 text
## 1                                                My economic policy speech will be carried live at 12:15 P.M. Enjoy!
## 2 Join me in Fayetteville, North Carolina tomorrow evening at 6pm. Tickets now available at: https://t.co/Z80d4MYIg8
## 3                                                   #ICYMI: "Will Media Apologize to Trump?" https://t.co/ia7rKBmioA
##   favorited favoriteCount replyToSN             created truncated
## 1     FALSE          9214      <NA> 2016-08-08 15:20:44     FALSE
## 2     FALSE          6981      <NA> 2016-08-08 13:28:20     FALSE
## 3     FALSE         15724      <NA> 2016-08-08 00:05:54     FALSE
##   replyToSID                 id replyToUID
## 1         NA 762669882571980801       <NA>
## 2         NA 762641595439190016       <NA>
## 3         NA 762439658911338496       <NA>
##                                                                           statusSource
## 1 <a href="http://twitter.com/download/android" rel="nofollow">Twitter for Android</a>
## 2   <a href="http://twitter.com/download/iphone" rel="nofollow">Twitter for iPhone</a>
## 3   <a href="http://twitter.com/download/iphone" rel="nofollow">Twitter for iPhone</a>
##        screenName retweetCount isRetweet retweeted longitude latitude
## 1 realDonaldTrump         3107     FALSE     FALSE      <NA>     <NA>
## 2 realDonaldTrump         2390     FALSE     FALSE      <NA>     <NA>
## 3 realDonaldTrump         6691     FALSE     FALSE      <NA>     <NA>
```

```r
names(trump_tweets_df)
```

```
##  [1] "text"          "favorited"     "favoriteCount" "replyToSN"    
##  [5] "created"       "truncated"     "replyToSID"    "id"           
##  [9] "replyToUID"    "statusSource"  "screenName"    "retweetCount" 
## [13] "isRetweet"     "retweeted"     "longitude"     "latitude"
```

```r
library(jsonlite)
library(httr)

url <- "https://www.dcard.tw/_api/forums/relationship/posts?popular=true"
res <- fromJSON(content(GET(url), "text"))
head(res, 3)
```

```
##          id               title
## 1 228422266 抱歉啊，阿嬤老了...
## 2 228425716    #圖文 順暢的女友
## 3 228422384        我的嘴砲男友
##                                                                                                                                                                                                                                        excerpt
## 1                               第一次發文，請多多指教。先來介紹一下我的家庭：小學三年級，我的父母離婚了。因為經濟能力問題，我媽沒辦法一次帶著三個孩子走，我是老大還有一個妹妹與弟弟。若只帶走其中一個對誰也不公平，所以我們全部都留在我爸這，
## 2                                   我女朋友有個非常強大的生物優勢，那就是順暢的消化道，只要吃多了，便意馬上就來了，而且只要來了就不能忍，這或許就是她的保養祕訣吧，像是吃火鍋的時候，她非常喜歡吃火鍋，然後火鍋很容易飽，她馬上會感應到便意，
## 3 1、我很少要求男友幫我拍照，可是出遊難免還是想要來個全身照，拍完之後，（我男友），：「為什麼你都把我拍的這麼醜...」：「啊妳就長這樣啊」（WTF），2.本身胸小但是還是算有隆起的小山丘（不用猜就是B），有一次男友載我去吃飯的路上，途中一直煞車～
##   anonymousSchool anonymousDepartment pinned
## 1           FALSE                TRUE  FALSE
## 2           FALSE                TRUE  FALSE
## 3            TRUE                TRUE  FALSE
##                                forumId replyId                createdAt
## 1 42851318-b9e2-4a75-8a05-9fe180becefe      NA 2018-03-04T15:40:06.549Z
## 2 42851318-b9e2-4a75-8a05-9fe180becefe      NA 2018-03-05T06:16:43.529Z
## 3 42851318-b9e2-4a75-8a05-9fe180becefe      NA 2018-03-04T15:54:02.672Z
##                  updatedAt commentCount likeCount withNickname
## 1 2018-03-06T01:30:43.481Z           78      6827        FALSE
## 2 2018-03-06T01:29:52.078Z           34      2362         TRUE
## 3 2018-03-06T01:21:50.390Z           23      1651        FALSE
##             tags topics forumName   forumAlias gender               school
## 1 HIDE_THUMBNAIL   NULL      感情 relationship      F 馬偕醫護管理專科學校
## 2                  NULL      感情 relationship      M                Green
## 3                  NULL      感情 relationship      F                 <NA>
##   replyTitle hidden withImages withVideos
## 1       <NA>  FALSE      FALSE      FALSE
## 2       <NA>  FALSE       TRUE      FALSE
## 3       <NA>  FALSE       TRUE      FALSE
##                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            media
## 1                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           NULL
## 2 http://i.imgur.com/JAUn4fa.jpg, http://i.imgur.com/HD6HQeG.jpg, http://i.imgur.com/5bk5jwy.jpg, http://i.imgur.com/ZHtMOop.jpg, http://i.imgur.com/0Vf9I2d.jpg, http://i.imgur.com/P4gglgU.jpg, http://i.imgur.com/JwhinGN.jpg, http://i.imgur.com/TpkFtFX.jpg, http://i.imgur.com/FSNJtvN.jpg, http://i.imgur.com/YBjQGpe.jpg, http://i.imgur.com/GBaRhLx.jpg, http://i.imgur.com/mLwhKhR.jpg, http://i.imgur.com/ICmdPVw.jpg, http://i.imgur.com/ohgJjss.jpg, http://i.imgur.com/LTWMlrH.jpg, http://i.imgur.com/HKVQdQ2.jpg, http://i.imgur.com/z4pxiwG.jpg, http://i.imgur.com/eqX0UMP.jpg
## 3                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                https://i.imgur.com/d5CRBtU.jpg
##   department
## 1       <NA>
## 2  greennchu
## 3       <NA>
```

```r
names(res)
```

```
##  [1] "id"                  "title"               "excerpt"            
##  [4] "anonymousSchool"     "anonymousDepartment" "pinned"             
##  [7] "forumId"             "replyId"             "createdAt"          
## [10] "updatedAt"           "commentCount"        "likeCount"          
## [13] "withNickname"        "tags"                "topics"             
## [16] "forumName"           "forumAlias"          "gender"             
## [19] "school"              "replyTitle"          "hidden"             
## [22] "withImages"          "withVideos"          "media"              
## [25] "department"
```

```r
fburl <- 
	"https://graph.facebook.com/v2.10/DoctorKoWJ?fields=posts&access_token=188730144854871|1lL4a4CTRymAHvoKxnJDQqvqVdc"

res <- fromJSON(content(GET(fburl), "text"))
head(res$posts$data, 3)
```

```
##               created_time
## 1 2018-03-05T11:00:00+0000
## 2 2018-03-04T11:58:40+0000
## 3 2018-03-04T04:32:20+0000
##                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           message
## 1                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          今年的台北燈節落幕了，雖然資源有限，但市府同仁和策展單位都拼了，每一盞燈、每一座裝置藝術，我們都用最大的誠意，希望能讓大家都感受到滿滿的幸福。\n\n讓我們用三分鐘，回味這九天的幸福，看見西區最美的一刻。\n\n台北旅遊網-2018臺北燈節\n智慧臺北 幸福生活
## 2                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     今晚，台北燈節就要告一段落，榮耀歸於所有辛苦的無名英雄們。\n\n很多公務員為了彩排昨晚的燈節大遊行，拼到凌晨三點；為了環境整潔，環保局同仁們守在每一個垃圾桶前，協助民眾分類；負責交通與治安的警察，也相當辛苦，堅守崗位直到燈節熄燈的最後一刻。\n\n感謝再感謝，除了感謝還是感謝，你們的努力，成就了這座光榮城市。\n\n台北旅遊網-2018臺北燈節
## 3 過去公園裡的遊戲場，我們以為把跟罐頭一樣千篇一律的遊具擺上去就可以了，事實上玩這些遊具身體不會更健康，但頭腦會更簡單。\n\n現在我們要把「共融式遊具」引進公園，我們讓當地居民與專家一起討論，接著找台灣本土的設計團隊來設計，讓每一座遊具都有獨特的主題與在地特色。\n\n共融式遊具最重要的目標，就是讓0到99歲都可以玩在一起，這一次全新啟用、佔地兩千坪的花博公園舞蝶共融遊戲場，我們還裝了台灣第一座「輪椅鞦韆」，讓身障朋友也可享受盪鞦韆的快樂。\n\n起初我也不懂什麼是共融式遊具，在議員質詢之後，我找了社會局許立民局長一起研究，從中我也學到一課：「設計是要花錢的」，台灣有很多優秀的設計人才，我們應該要用公共工程來培養台灣的設計能量，給他們更多舞台發揮。\n\n目前我們已經蓋好17處共融式遊戲場，明年底前要達到31處，每區至少都要有一座。\n\n大家不用再羨慕國外有這麼多好玩的遊具可玩，從現在開始，台北市的公園遊具會更有創意。\n\n#進步價值光榮城市\n#共融式遊戲場\n#全台首座輪椅鞦韆\n工務話台北\n\n---\n花博公園舞蝶共融遊戲場\nhttps://www.travel.taipei/zh-tw/featured/details/13758
##                                 id                      story
## 1 136845026417486_1259930147442296                       <NA>
## 2 136845026417486_1259131887522122 柯文哲 added 4 new photos.
## 3 136845026417486_1258854180883226                       <NA>
```

```r
names(res$posts$data)
```

```
## [1] "created_time" "message"      "id"           "story"
```

