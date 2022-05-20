---
author: "Poovamraj T T"
title: "Native > Flutter > React Native"
date: "2018-03-12"
description: 
tags: ["mobile app", "hybrid app", "flutter", "react native", "android"]
ShowToc: true
---
This blog is aimed at people who haven’t heard of flutter and would like to take a shallow dive into it

Many of you already would have heard about this new Google’s framework. It was proposed and the beta was released a few weeks back. It is a framework in development. If you haven’t heard of it, then the next sentence I am going to tell will mostly make you close this post

it is a framework for cross-platform mobile development
![No!](/no-bird.gif)
    

As we all know there are a lot of cross-platform development frameworks but none beats the user experience of a natively developed application. A few months back here I was trying to appeal for React Native. But when I took it for a full spin for a fun project. I fell flat on my face.

There were many shortcomings when it came to React Native. Since mobile applications heavily depend on swipe-based user interaction and React Native heavily depends on a bridge that makes the JS code run on the native engine. This caused a lot of janking due to bottleneck. List Views using React Native was a nightmare. This was all based on that one bridge that helped the JS code pass on to the native interface and render natively. This bridge was a huge problem. Burn that bridge!!

**How is flutter different from React Native and native development**

1) If you have heard of the new framework called Svelte for JS which compiles your code to vanilla JS. That’s how flutter is different from React Native. It cuts off all the hassle and instead compiles your code ahead of time. So no mess for the user, no mess for the developer, it would be the job of the framework maintainers to make sure flutter compiles into an optimized proper native instruction set. how neat is that! Unlike React Native deviously in its name suggesting it runs on native but in real runs over a JS engine which communicates with the native.

2) If you haven’t experienced hot reload in your life as a front end developer, you should seriously do it at least just for the fun of it. It is like finding the holy grail of front end development. All the code changes that you do are reflected on your device just by the click of ctrl+s. How cool is that? It is like your code is a paintbrush and all your strokes are reflected instantaneously with a ctrl+s. And flutter supports this, but so does React Native, ReactJS and many other. But an Android instant run can’t even be compared to a hot reload.

3) If Flutter could provide what it promises. Then similar to web development, we wouldn’t be needing double the people writing code for mobile apps. The code base could be shared and our release cycles and productivity would skyrocket.

4) Flutter provides widgets. Being a mobile developer since the beginning and having to write my own widgets from scratch like a web developer, felt weird when I developed using React Native. Flutter promises set of widgets that are provided by the framework itself. This (at least for me) is a huge plus

**Disadvantages**

1) As I was getting a little excited about this framework, There was one big blow that raised a huge concern. The language used for this framework, DART, is single threaded. I can’t wrap my amateur head over the fact that any serious programming language could be single threaded (Looking at you Javascript ಠ_ಠ ). But to be honest there seem to be alternatives provided by DART to the highly vulnerable traditional threading. but as of DART 1, shared memory threads are not possible.

2) Does not have any specialized layout language to define your UI. This is something similar to the current situation of iOS developers where they have to define their View using code or the alternatives suck. How awkward is that iOS developers? (asked the Android developer from the comfort of his constraint layout). Having a separate layout language to define your views is beneficial in many ways but it is most helpful in separating your business logic from your Views.

Still not convinced? Sit back and listen to this cool metaphor I thought of while driving. Having a layout language in your front end framework is like having a hard divider in the road your driving. When there are no dividers, Even though you know that it is the best practice to drive on the left side(or right side, depending on where you are from) of the road and most of the time you do drive on the correct side. There are always those rogue drivers or special cases where the vehicles pass to the other side. Having a layout language is like having that divider. You can be assured that in no case does your code goes spaghetti because of it.

3) Could Web take over before Flutter could raise to its power? We all mobile developers know that one day the web will take over the front end of mobile applications, ruthlessly, mercilessly, just like it swallowed the desktop applications. But it is a matter of time. It will take sometime before Flutter could create a community and have a stable foot over the mobile platform even if it has very high levels of awesomeness. But could Web take over before flutter does this? There are already cool websites popping out that challenges the boundaries of Progressive web apps. Only time could answer this question.

All that said. Talking glory about Flutter and saying it can save us from the tyranny of maintaining 2 code bases at this stage is like one of those statements which say DRINKING COFFEE CURES CANCER. Flutter is in its early stages with very little data set/experience even to be considered to be used in serious or existing code bases. It is an attempt and hopefully something that will improve lives of the developers and in turn the users.

But damn, Now we mobile developers have a new toy to play with and I know which framework I am going to use for my next fun project.

[Originally Published in Medium](https://medium.com/@poovamraj/native-flutter-react-native-749dd206c654)