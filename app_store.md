```python
from app_store_scraper import AppStore 
import pandas as pd 
import datetime as dt
import numpy as np
import json
```


```python
# app_id, region, no_of_reviews, date
def get_app_info(app_id, region, no_of_reviews, date):
    app_store = AppStore(region, app_name=app_id)
    app_store.review(how_many = no_of_reviews, after=date) 
    df = pd.DataFrame(np.array(app_store.reviews),columns=['review']) 
    df2 = df.join(pd.DataFrame(df.pop('review').tolist())) 
    df2.to_csv('tiktok_reviews3.csv',index=False)
    return True
```


```python
get_app_info("us", "tiktok", no_of_reviews=10, date=dt.datetime(2022,1,1))
```

    2022-07-16 03:32:14,793 [INFO] Base - Searching for app id
    2022-07-16 03:32:18,467 [INFO] Base - Initialised: AppStore('tiktok', 'us', 36)
    2022-07-16 03:32:18,470 [INFO] Base - Ready to fetch reviews from: https://apps.apple.com/tiktok/app/us/id36
    2022-07-16 03:32:18,799 [ERROR] Base - Something went wrong: 'data'
    2022-07-16 03:32:18,801 [INFO] Base - [id:36] Fetched 0 reviews (0 fetched in total)





    True




```python
st = []
tiktok = AppStore(country="us", app_name="tiktok") 
tiktok.review(how_many=10)
st.append(tiktok.reviews)
```

    2022-07-16 03:32:18,831 [INFO] Base - Searching for app id
    2022-07-16 03:32:22,677 [INFO] Base - Initialised: AppStore('us', 'tiktok', 835599320)
    2022-07-16 03:32:22,681 [INFO] Base - Ready to fetch reviews from: https://apps.apple.com/us/app/tiktok/id835599320
    2022-07-16 03:32:23,153 [INFO] Base - [id:835599320] Fetched 20 reviews (20 fetched in total)



```python
tiktok.reviews
```




    [{'userName': 'Nasim thanks tik tok',
      'date': datetime.datetime(2022, 6, 3, 20, 32, 9),
      'review': 'I am a tik toker and I’m not famous or anything but I love TikTok I love how everyone comes together. From many with disabilities to discovering new things and so much more everyone has someone who loves them and I love that. I love all content from animals to fashion. Trendsetters and so much more TikTok has changed the game in a way that cannot be copied by any other platform. Given everyone an opportunity in this world to shine. Everyone has fame and fame is something chased by many on every level. TikTok is a safe place for some therapeutic for many and a place for the socially conservative or anti social to come be free. However I think there should be some changes such as the protocol to TikTok removing videos of creators for nudity just for doing the same trend a verified user does. Favoritism maybe call it whatever but something is definitely fishy about this because I’ve seen so many get banned blocked and removed for shaking their bottoms with sweat pants on but the verified users or people with more followers get away with it. Also if your over 18 you should be able to post whatever content to extent long as your not promoting anything inappropriate. My biggest issue is that I find TikTok allowing only certain creators to be nude or inappropriate but if I were to wear panties and do a dance it would be considered nudity or whatever please fix that it’s not fair.\nle',
      'isEdited': False,
      'rating': 5,
      'title': 'TikTok For any age'},
     {'userName': 'Novicakes',
      'date': datetime.datetime(2022, 5, 1, 15, 39, 25),
      'review': 'Honestly tiktok  is a great app but is overall very addicting I feel like the preview of the app looks very nice but once you download the app it takes over daily task and makes them harder. \nI love being able to share videos and watch tons of people’s creations, but compared to what the preview tells you the app is very different you get banned for small things and have your videos taken down but there’s nudity all over  tiktok that has yet to be taken down, I get it’s just a body but kids shouldn’t have to experience such things like that yet there are also very rude people and they shouldn’t have to be bullied either. Also  tiktok  can honestly take over small easy task like cleaning  it’s honestly very addicting and all you do after you delete it is download it back, Some people aren’t able to small task as easily as others and tiktok just makes that harder for them like lack of motivation is a real struggle and staying up all night isn’t something that helps. When you reach  10k+ you get creator funds but honestly you don’t get that much money I get it’s a 1-2 minute video but lots of influencers and artist etc work hard on a lot of those videos just to get like 16$ on a video. \nAnd I’m not trying to blame the app creators it’s basically the people on the app but this is just the stuff that happens on the app and needs to be banned and the creators need to start getting more money than what they actually get.',
      'isEdited': False,
      'rating': 4,
      'title': 'Amazing app (Bad addiction)'},
     {'userName': 'GreenJewel123',
      'date': datetime.datetime(2022, 5, 27, 22, 36, 7),
      'review': 'Instead of having only a few users get updates at a time and doing rollouts, I feel like everyone should get the updates at the same time. I still haven’t gotten the option to repost videos or create playlists while some of my friends have. But then they also have the issue where I’m able to upload the 3 and 10 minutes videos and create stories but they haven’t gotten those updates yet. I also feel like we should be able to schedule our posts on the app. I know we’re able to do it on the desktop but most of us use the app on our phones so it doesn’t make sense that we wouldn’t be able to have that option. On tumblr we’re able to put our posts in a queue or schedule them to be released at a specific time. If we had that option it would make it easier to make posts consistently without us having to worry about timing.\n\nI really enjoy the new Studio that’s been implemented, however I believe a major flaw in it is that when we decide to edit a clip and start over is that we can’t hear the section of audio of said clip while re-recording. Before Studio we had that option automatically applied so when we record something again, we can make sure the timing is right, especially if we’re lip syncing. Now we can’t hear anything while recording again so we have to hope for the best or just start the entire video over from scratch.',
      'isEdited': False,
      'rating': 4,
      'title': 'Mass updates, Schedule posts, & Studio'},
     {'userName': 'Poom Pooh',
      'date': datetime.datetime(2022, 1, 18, 4, 7, 26),
      'review': 'I really enjoy this social media platform. The app is amazing and a great way to socialize with people all around the world. it’s all wonderful. What I do have a problem with is how quick this app can take down a harmless video. And yet the traumatizing video of a dog being ripped to shreds in broad daylight seemed like it took forever to be taken off. I remember getting one of my videos taken down because it had one swearword in it. It got taken down a day after I posted it. But it took groups of people to make videos under the sound for the video to get taken off of tiktok. A lot of people complained about being disturbed after seeing the video. I mean how could you not? It was nothing but sick. I won’t going to detail about it. This isn’t the first issue either. It took a good week for a A video with a edited audio from the game. The person who made it made it seem like the child was having sex with a character that was supposedly known as an adult. Either way that doesn’t make it OK. They even made two videos just with a different character. There’s even an account still up today where there’re making animation videos about the child and the character dating. All I’m saying is I love this app. I’ve gained a lot of confidence from it and I’m happy with my account. I just think tiktok needs to be a little bit quicker and concerned about the gruesome videos and disgusting ones uploaded.',
      'isEdited': False,
      'rating': 4,
      'title': 'It’s amazing. Just needs a bit of a dim'},
     {'userName': 'nobody >3',
      'date': datetime.datetime(2022, 4, 30, 10, 16, 15),
      'review': 'Awesome app so Many creative people lives are great watching also the videos people make are cool too I just wish I could get more in my room not sure how this banning is getting out of hand just because of a sad person reporting you tiktok bans the account noway to talk to tiktok also I’m not getting any likes on nothing ? I honestly think if you have high numbers and have friends with the same you are good for a viral just be fair tiktok I don’t think it’s much to ask things just aren’t fair across the platform your guidlines I see half naked women men too make it a guidline to wear clothes let’s see how many gifts likes and people they get in their rooms then sad people have to promote them selves this way let the little guy have veiws likes gifts and some fun if I get banned I will not come back it isn’t worth it to me to start over at a thou takes a long time and most viral vids can be the dumbest ever rooms with one l plus and no creativity it’s all about the big numbers sticking together it isn’t they deserve it it’s they have so many followers you can’t compete with it just make it fair across the platform everyone should be the same let the people decide stop with them having so much control I live tik tok but when your creating and your room has three people in it all the time it’s discouraging why perform in a room with noone in it ?',
      'isEdited': False,
      'rating': 5,
      'title': 'Live'},
     {'userName': 'ljk55Chevygirl',
      'date': datetime.datetime(2022, 5, 10, 2, 13, 27),
      'review': 'I am enjoying this app so much ... I am completely entertained ... although I am new to this ... someday I wanna make a video Well January 2021 is here... although I am enjoying this app... I don’t appreciate being censored and told that I have shared enough when I know it is censorship I am enjoying this app very much.. but why is it that when I follow someone that I stop seeing them in my “following” section?!?!? Time for another evaluation... ok .. so, I do enjoy TikTok very much... I enjoy having the ability to follow and possibly to help people on here Yes... I am so glad that I have had the opportunity to meet sone awesome people on this app I enjoy this app but I don’t understand why I don’t see people that I am following for extended periods of time and I have to go and search for them to catch up!!!! Is this how it works? When I follow an account they stop showing up for me? I have to go look them up.. otherwise I do enjoy this app Good times Well here is another eval…. So, yes I enjoy this app! I like this app\nMay9, 2022\nI don’t understand why someone on here says see part 2 at the link below… I go to it ( NEVER TGE SAME ONE TWICE) and it is a private account… I NEVER GET ACCEPTED if I follow… besides ( IF I DID) it wouldn’t matter anyway… BECAUSE THE NEXT ONE LINKS TO A NEW ACCOUNT… it is so stupid and I just don’t get it!!!!',
      'isEdited': False,
      'rating': 5,
      'title': 'My thoughts about TikTok'},
     {'userName': 'Shalanda Albert',
      'date': datetime.datetime(2022, 1, 22, 20, 24, 30),
      'review': 'I like TikTok. I feel that the people here are real and that’s what I need. \nWhat I don’t like is how TikTok will mute your videos. It seems they do it when you begin to grow fast all of a sudden you began to slow down and I feel they put your videos out when they want to. I’m self employed, I have a son graduating this year,I’m writing a book and looking to relocate so I can’t put videos out at a certain time or stay current on the trends but my videos should be pushed as well. I have a video that was my first 1.5 views and when it got there TikTok muted it. Why? When I can’t post new content I will repost an old video to try and keep my followers. The other videos haven’t been muted but they muted the growing ones. This has happened so much at first I almost gave up but because of the people on here, I stayed. I don’t feel I’ll ever go viral but honestly once I can give more I will however when I was giving my videos was being muted and continued to get violations. I’ve had to constantly appeal things in the beginning. Like I said I love the people on TikTok don’t know how happy I am with the people who get paid to watch our videos and get paid. They want you to pay to get boosted but I want to earn my followers and likes. I did this to help with my mental and at first it began to effect it when you’re trying so hard but kept getting muted but now I’m learning.',
      'isEdited': False,
      'rating': 4,
      'title': 'I love the honesty of the people on TikTok'},
     {'userName': 'Kaley Bradshaw',
      'date': datetime.datetime(2022, 6, 25, 23, 27, 7),
      'review': 'Writing this review I feel bad giving only 3 stars, considering I’m literally obsessed with this app, but there are some major problems (in my opinion) with it. First of all, the app is addicting. I’ve lost so many hours watching TikTok that I could’ve been studying, sleeping, etcetera. I know it’s partially my fault, but I still think more can be done to prevent users from staying on the app for long periods of time. The second thing is about updates. I have multiple TikTok accounts. Every account has a different version of updates. I am also always behind on new updates because of this. When I go on the app store most of the time it reads “open” instead of “update”. I’m very frustrated when I can’t participate in trends because I’m still stuck with a version that is 2 months behind all of my friends. I understand the app isn’t perfect but if there’s an update it should be available to all users at the same time. I know that my phone isn’t the problem, as other users have experienced the same thing as me. Other than this and the fact that I can’t stay off of it, TikTok is a great app and sometimes can be very uplifting and kind. The app allows you to express your creativity and learn to do things you would’ve never thought you would need to know. I believe if these two things could be improved, then TikTok will be the perfect app for people to use as a way to get involved and be their true selves.',
      'isEdited': False,
      'rating': 3,
      'title': 'TikTok'},
     {'userName': "Taylor's Playlist",
      'date': datetime.datetime(2022, 1, 23, 17, 1),
      'review': 'I’ve been on TikTok since 2019 and it has its ups and downs. I had a some videos go viral which is pretty cool, but the algorithm is so unpredictable sometimes that most of my content is barely seen even with the use of trends and huge amounts of effort. My biggest complaint though is how broken the moderation system is. It’s unusually strict and even unpredictable. Even when I follow guidelines I still get content taken down, which is confusing and frustrating. On other platforms such as Twitter, Insta, etc., I have never gotten any of my content taken down or flagged ever. I’ve had several TikToks taken down for unknown reasons and the reasons listed are usually vague or wildly incorrect. For example, I used a fake animal prop and it was taken down for “violence” even though I made a disclaimer in the video stating it was a prop and no actual animals were harmed. Despite this, my appeal got rejected so I emailed customer service, which itself is a whole other headache to deal with. It took them WEEKS to respond and all they did was give me a generic response to click the appeal link, which I already told them that I did. It’s as if they didn’t read the actual email at all. Overall, I feel like I have to walk on eggshells now when I post content. It takes the joy out of it. TikTok, if you’re actually reading this, PLEASE fix this. You are literally hurting the community’s content creators.',
      'isEdited': False,
      'rating': 3,
      'title': 'Oh no. The moderation system. It’s broken!'},
     {'userName': 'Zanna .',
      'date': datetime.datetime(2021, 6, 21, 23, 34, 58),
      'review': 'For all of the hype that surrounds TikTok, it is an incredibly interesting app that plays a major role in the life of most adolescents today. It can create unique spaces of community on the app, and provide content for people to talk about, share, and bond over outside the app itself. However, from my own experience, I would rate the app a 3 out of 5. The fact that the For You page provides a constant stream of new content is a brilliant design choice to get people to spend longer on the app, it can often feel like the user does not have agency over what they are seeing. Additionally, fears about being on a different ‘side’ of TikTok than peers could be a source of stress or concern for some adolescents, adding to potential mental health effects social media can have. Most of the design of the app is intuitive once the user has been on it for a little bit, and while the privacy settings are not front-and-center, they are available so that adolescents can have the content that they view tailored somewhat to not include inappropriate content and to promote healthy app usage, but allowing a parent to have potential control over being able to extend time using the app must feel like an invasion of their privacy. However, without an external source of monitoring, it can be very easy for adolescents, as well as adults, to become compulsive TikTok users who only find sporadic joy from the content they watch.',
      'isEdited': False,
      'rating': 3,
      'title': 'Social Work student here!'},
     {'userName': 'fkxjudiwofk',
      'date': datetime.datetime(2022, 5, 16, 3, 49, 49),
      'review': 'I never do reviews for apps, but I must for this one because I’ve never been more entertained and worse more time on a single individual app like I have TikTok!!  It’s jus so fun and entertaining, so many dif kinda people on there si everything is hand made for every single person to find similar interest to their own and each account holder/tik tok user has their for you page, which are page(s) curated to each individuals interest etc; I must say the curation and accuracy of the algorithm of this app is right up their with Twitter; but I’d say even better/high than Twitter. Twitter gets pretty repetitive, that’s why I love tik tok; TikTok is always showing brand-new stuff all the time and doesn’t repeat interests!! Such as for; it doesn’t repeat anything you’ve liked or interacted with, even the ads are new every time but you will have your occasional “oh I’ve seen this one before” ad! AD; not video!! Video is always brand new never seen before, content is always updated and curated to you personally daily!! I love this app I could on & on; \n\n  Long sorry short; this app never misses; you’ve got your favorite personal interest; updated daily with a humongous variety; top tier comedy on this platform too; it’s the main social platform these days. 10/10',
      'isEdited': False,
      'rating': 5,
      'title': 'I spend 13 hours a day on this app'},
     {'userName': 'xbjxjdndndn',
      'date': datetime.datetime(2022, 6, 14, 4, 8, 1),
      'review': 'I keep getting banned for no reason on this app and I’m getting sick of tired of it I want just a regular account that gets abuse I don’t want no banding processes in my account I hate how my account gets banned every single time I make a new account and now I can’t even make a new account what should I do I ran out of resources and I just don’t know what to do I wish the banding thing was never there so I can just have a normal TickTock account I know it’s there for safety reasons that TickTock has a band button or a record button but people are using it for a vantage to make people get banned for no reason it’s a good app that I read it a 4 i’m just saying like the band in the report button thing is not good just don’t report people for no reason report people if they’re doing bad things or abusing or something like that i’m not trying to do anything to TikTok I would just like them to do something with the band and important but and help me get my account back this band button got me banned four times and I’m getting sick of tired of people banding people for no reason it’s just not fair I feel like they’re just jealous of our followers and it’s getting on my nerves how people just keep banding us we shouldn’t be banned for this I know I’m 12 but like I would just like to not have my account banned by people that think it’s funny',
      'isEdited': False,
      'rating': 4,
      'title': 'And getting banned'},
     {'userName': 'dorientina',
      'date': datetime.datetime(2022, 5, 7, 0, 20, 58),
      'review': 'I started tiktok for fun and just to watch never post! Here I am 2.7 milion followers later! I love tiktok! We love tiktok we are up to 3.7 million followers like whattt??!! Thank you for helping us showcase his little talent of cooking! And having found so many supporters who enjoy his videos!!! Update! Thanks to tiktok and all the amazing followers we are at 4.2 milion!!!!!! Update! 4.7 milion followers! Thank You TIKTOK FOR THE OPPORTUNITY! Still loving Tiktok! UPDATE! We are at 4.8 milion (how crazy?) this is Qibeen a crazy journey thank you tiktok for the platform! Update! 5.4 milion! So unbelievable he has come this far with TikTok! Grateful! We love TikTok!WE LOVE TIKTOK! 5.8 milion Update ! 6 milion fans WOW! We still love using TikTok up to 6.2 million but what a crazy and blessed year we had with TikTok! It’s been a while since we updated but we are at 6.8 milion like it’s so crazy liek to think all these people watch our son! Sometimes views go up and sometimes down but that’s Tiktok! Update 6.9!we love Tiktok! Thankful for 7 million Tiktok! Update 7.1 million fans of eee! We love Tiktok! We’re at 7.2 milion and tho our fans are mixed on his account some love him and some just like to see him get hurt but as long as he makes ppl laugh (cause that’s what our goal is to make people happy) and he loves it which is the best part!UPDATE 7.6 milion',
      'isEdited': False,
      'rating': 5,
      'title': 'CEO eee'},
     {'userName': 'Nanamills51',
      'date': datetime.datetime(2022, 6, 23, 15, 7, 13),
      'review': 'I can say what I feel about what I don’t like about what the president is doing to our country without being band from my account. I can say how I feel about my love for Jesus and not get band. I can say how I feel about my fears of the Covid and without getting band from my account. I can say how I feel about my fear of getting the vaccine shot without getting band from my account. At first I was completely against getting the shot, but after I was aloud to hear all sides . I decided to get them. I was completely against them to start with simply because Biden ,dr foulice ,( I know I didn’t spell his name right but I don’t care) and Harris are soo dishonest , with us , and flat out lied to the American people so much that we couldn’t and can’t trust a word they say! Then he starts to demand us to get it while letting everyone at the border walk in with nothing. He has shown the American people that he doesn’t care about us at all, if we live or die while he gives everything to anyone coming in at the borders. So thank you for letting me be able to make videos expressing how I feel! I am a Born again Christian, and I love my God given Freedom of speech! I’m 70 years old so I’m ready to go to Heaven, it’s a shame Biden isn’t! Thank you so much tiktok',
      'isEdited': False,
      'rating': 5,
      'title': 'I like tiktok a lot better than Fb'},
     {'userName': 'Random Chan',
      'date': datetime.datetime(2022, 3, 8, 16, 18, 21),
      'review': 'ive used this app since musically, and honestly its grown to be a part of my life. the platform doesnt selfishly do everything they can to keep people on the app and even has an ad to get people to make sure theyre taking breaks. (“HOLD ON, youve been scrolling for way too long now!!” lol) the app has so many different communities and has helped new artists get out there and even made brand new artists songs go viral. the app has so much potential. the problem is their system and the way the fyp works. what happens is, when one of your videos are viewed multiple times by people and they like it or comment, the video is shared to peoples pages with similar interests. this means that if the first few people that see your video are uninterested and scroll, the video likely wont show up on many more for you pages. another system they have that is flawed is when you upload a video from your camera roll. when you upload a video from your camera roll, tik tok looks for similar videos due to plagarism. if they find a video similar or the same then they mark it as plagurism and share it to nobodys fyp. this is shadow banning. many peoples videos are put down with this feature. other than that, this app is a well programed and far more entertaining than other social media.',
      'isEdited': False,
      'rating': 4,
      'title': 'like most social media, but has flaws.'},
     {'userName': 'HELLOOOOOOOOOOOOOO IM MOOOOOON',
      'date': datetime.datetime(2022, 5, 27, 0, 41, 9),
      'review': 'I would give this 5 because I love tiktok I love being able to talk to my friends to share videos to post & see my views and likes to know that I’m doing just okay to see my feed back to know that what I’m doing is right and I’m not alone but there’s are some bad parts about being a tiktoker or well me a gachatoker so let’s get into the bad parts there’s a lot of hate that comes with posting a lot of stuff you have to do and then you over think what are you doing wrong to get so much hate what are you doing right to have so much support & if your like me you don’t think you deserve so much you think your videos are cringe when a lot of people says you aren’t when you wanna do a face reveal but tiktok makes you so insecure there are videos with the sound “this you, this you?” And people exposing there haters like what and now you got a lot of people like me addicted, sleep deprived, and just feeling horrible & you also let women twerk, be naked, be in a bikini, breastfeed, there boobs out and apparently this is a children’s app yes nothing is wrong with breastfeeding if this was an adult app cause it’s just showing a mothers Journey but there are 10-15 year olds seeing this that is very inappropriate if you ask me and you ban people for no reason if anything ban those people also TOO MANY UPDATES like just no they are so bad like please stop updating the app thank you<3',
      'isEdited': False,
      'rating': 3,
      'title': 'Amazing (buttttt)'},
     {'userName': '🙏✝️❣️',
      'date': datetime.datetime(2022, 6, 23, 4, 37, 8),
      'review': 'The first time I heared of tiktok I wasn’t sure what it was but as I made an account and watched livestreams and watched tiktok videos I just never thought I’d join let alone make my own tiktok videos and here iam doing just that cause tiktok is place you can express yourself and make new friends and share your hidden talents and share your joys hopes and dreams and sadness with family and friends and even great people GodBlessYou 🙏👩🏻😃👋🏻come check it out ♥️👋🏻😃👩🏻cause it’s been blessing for me hope it is for you too 🙏💕If your feeling alone or just trying to find away to meet or inter act with people but your busy working or go to college or just busy with taking care of family been parents or sister or brother a grandparents or auntie or uncle or just friend this could be for you come check it out you might find video topics that interest you in cooking or painting music dancing Comedyand so many more hope to see you checking my christiantiktok videos out GodBlessYou 🙏💕😊👩🏻👋🏻I’ve also noticed so many beautiful people on tiktok up lift other Tiktokers in time they truly needed prayers or encouragement kindness to help them during difficult time in there life . Kindness can truly go along way GodBlessYou TikTok‘s got it going on ✨🕊✨💕✨😊🙏✨',
      'isEdited': False,
      'rating': 5,
      'title': 'Love 👩🏻♥️🙏tiktok🙌🎶🥰'},
     {'userName': 'vee33$',
      'date': datetime.datetime(2022, 4, 14, 0, 37, 1),
      'review': 'Hi my name on tiktok is mosthated_vee34 and I am so in love with this app only thing I have a big problem with is the fact we get banned for things we really didn’t do and blocked and I really feel it’s not fair the community guidelines are kinda destroying people pages because it’s people like me who work hard to build they page and keep being blocked and banned for no reason the kids and the adults who act like kids and the fake pages are taking over and it’s hurting and affecting a lot of great creators like myself I feel like banning people pages should not be a option especially when we over 10k followers we work hard to build our pages and we don’t intentionally try to hurt or harm anyone but then people really say a lot of mean things to us when we are live I had people wish death on my kids and me call me trans sexual and I’m a girl and we not suppose to defend our peace or ourselves but they can come on our live and say rude and mean things to us I have been blocked for someone calling me the N word and it really hurts cause I wanna turn this into a career and I’m being held back by fake pages and crazy rude people please help us creators who are there for what it is have some type of peace other than that I love it thumbs up',
      'isEdited': False,
      'rating': 5,
      'title': 'I love tiktok'},
     {'userName': 'enhpad13',
      'date': datetime.datetime(2021, 12, 15, 19, 23, 36),
      'review': 'I love TikTok; it is one of my favorite apps. However, TikTok randomly asked me to confirm my age, for some reason (which wouldn’t normally bother me because I had already confirmed it before),  so I confirmed my age. I put in my real date of birth (I’m 13 years old) and TikTok made my account private, made it to where people are unable to duet, stitch, or download my videos, and I can neither send nor receive messages. I completely understand that TikTok doesn’t want young children to get access to the app and post videos with their face or make unintelligent choices, but I have not done anything against TikTok’s policies or spread any negative energy. I am unable to send videos and messages to my friends or receive videos and messages from my friends. This has also happened to one of my old friends; someone reported him for being under the age limit (he is 13 years old) and TikTok private’s his account. I completely understand if you want people who are 13 years of age or younger to have privacy and not share personal information, but it doesn’t make sense that there are only some people (around 13 years old) that are being forced to have their accounts private’s when others do not also have to go through this. Thank you for taking the time to read this (I will change my star-rating to a 5/5 stars if this issue is fixed).',
      'isEdited': False,
      'rating': 3,
      'title': 'The app is astounding, but...'},
     {'userName': 'Suazo Sofia',
      'date': datetime.datetime(2020, 12, 29, 3, 58, 34),
      'review': 'Okay, here’s my review. This APP IS WONDERFUL. But there are some down sides to it. So, I deleted this app once but I wanted it back so I can use it on my spare time. So I just got it back and apparently I can’t get back into my old account. I saved all the data but the password doesn’t work. I’ve tried a bunch of times. It’s probably a bug. Anyways, my second “but” is that even if you don’t want an account and your trust trying out the app, don’t pull up the pop-up that says “SIGN UP” or “LOGIN IN”. I honestly don’t want an account for many reasons. Bullying, mean comments, inappropriate things, ext. At this time-period, you don’t have anywhere to be, or anything to do besides hang with your roommates (roommate), family members, or yourself. Trust me, it’s tough. But at this point social-media is our life now to figure out things and to learn more. (This probably has nothing to do but I’m trying to give ideas and my opinions). Sometimes I try to not open this app up because I don’t want to see the pop-up where it says to “SIGN IN” or to “LOGIN IN”. Please don’t get me wrong but this app is incredible because I use it on other devices. But this device I use daily needs this app! Thanks for letting me share my review. Hope it’s well enough for ideas. Stay safe! Happy Holidays!!!\n\n-Your fellow TikTok Fan.',
      'isEdited': False,
      'rating': 4,
      'title': 'Definitely A Great App But.....'}]




```python
for list in st:
    for i in range(len(list)):
        for dict in list:
            js_obj = json.dumps(dict, indent=4, sort_keys=True, default=str)
            with open("sample1.json", "w") as outfile:
                outfile.write(js_obj)
```


```python
import pymongo
```


```python
with open('sample1.json') as file:
    file_data = json.load(file)
```


```python
client = pymongo.MongoClient("<YOUR MONGODB CONNECTION STRING>")
db = client.new_db
```


```python
reviews = db.reviews
```


```python
file_data
```




    {'date': '2020-12-29 03:58:34',
     'isEdited': False,
     'rating': 4,
     'review': 'Okay, here’s my review. This APP IS WONDERFUL. But there are some down sides to it. So, I deleted this app once but I wanted it back so I can use it on my spare time. So I just got it back and apparently I can’t get back into my old account. I saved all the data but the password doesn’t work. I’ve tried a bunch of times. It’s probably a bug. Anyways, my second “but” is that even if you don’t want an account and your trust trying out the app, don’t pull up the pop-up that says “SIGN UP” or “LOGIN IN”. I honestly don’t want an account for many reasons. Bullying, mean comments, inappropriate things, ext. At this time-period, you don’t have anywhere to be, or anything to do besides hang with your roommates (roommate), family members, or yourself. Trust me, it’s tough. But at this point social-media is our life now to figure out things and to learn more. (This probably has nothing to do but I’m trying to give ideas and my opinions). Sometimes I try to not open this app up because I don’t want to see the pop-up where it says to “SIGN IN” or to “LOGIN IN”. Please don’t get me wrong but this app is incredible because I use it on other devices. But this device I use daily needs this app! Thanks for letting me share my review. Hope it’s well enough for ideas. Stay safe! Happy Holidays!!!\n\n-Your fellow TikTok Fan.',
     'title': 'Definitely A Great App But.....',
     'userName': 'Suazo Sofia',
     '_id': ObjectId('62d1e535b4bf56b293aa4ec2')}




```python
reviews.insert_one(file_data)
```




    <pymongo.results.InsertOneResult at 0x7f45bc4fd480>




```python
# DONE
```


```python

```
