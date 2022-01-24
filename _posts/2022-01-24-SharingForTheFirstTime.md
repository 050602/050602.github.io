
---
layout: post
title: 第一次分享-ECS战斗拆分思路（一）角色
date: 2022-01-24
categories: blog
tags: [技术分享]
description: 分享一下自己的想法，顺便与大家一同交流
---

已知ECS思想，

把任何事物，拆分成Entity System Component

需要先思考一个角色有哪些基本要素

>1. 它有一个基本的数据来描述它的存在，它是人，还是怪物，还是NPC之类
>2. 它有一些常见的角色属性，HP，Mp，Attack，Dfen，在角色进行战斗时，获取角色的数据，进行公式计算
>3. 它能显示在屏幕里，有一个VO，管理着它的显示，隐藏。。。
>4. 它有基本的位置描述信息，描述他在世界的哪个位置
>5. 技能，AI，Buff，逻辑。。。等等

根据具体功能，拆分出对应的System

比如
>1. 移动管理
>2. 技能释放管理
>3. AI管理
>4. 伤害管理
>5. 。。。等等

于是代码大概这样写

```javascript
创建一个Entity

然后为Entity添加LifeCom，AttrCom，VoCom，PosCom

移动System 关注 Entity的 VoCom和PosCom
技能System 关注 Entity的 AttrCom，SkillCom，HurtCom
AI System 关注 Entity的 AICom，AttrCom，PosCom，SkillCom
```
每个系统只关心关注的Component，其他一概不管，各司其职

就做到了逻辑和数据完全分离

欢迎各位来我的个人博客观光，希望从今天起，持续输出一些自己脑子里有的东西，也希望各位不吝指教

[啊安的个人博客](https://050602.github.io/)