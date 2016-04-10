---
title: 产品等级结构与产品族
id: 109
categories:
  - 设计模式
date: 2015-01-16 09:35:32
tags:
---

在理解抽象工厂模式之前，先了解两个概念：
1.产品等级结构：产品等级结构即产品的继承结构，例如一个抽象类是冰箱，其子类有海尔冰箱、TCL冰箱，则抽象冰箱与具体品牌的冰箱之间构成了一个产品等级结构，抽象冰箱是父类，而具体品牌的冰箱是其子类。这是从纵向的角度来看。
2.产品族：在抽象工厂模式中，产品族是指由同一个工厂生产的，位于不同产品等级结构中的一组产品，例如海尔电器工厂生产的海尔电视、海尔冰箱，海尔电视位于电视产品等级结构中，海尔冰箱位于冰箱产品结构中，海尔电视、海尔冰箱构成了一个产品族。这是从横向的角度来看。
当系统所提供的工厂生产的具体产品并不是一个简单的对象，而是多个位于不同产品等级结构、属于不同类型的具体产品时，就可以使用抽象工厂模式。
抽象工厂模式与工厂方法模式的区别在于，工厂方法模式针对的是一个产品等级结构，而抽象工厂模式需要面对多个产品等级结构，一个工厂等级结构可以负责多个不同产品等级结构中的产品对象的创建。当一个工厂等级结构可以创建出分属不同产品等级结构的一个产品族中的所有对象时，抽象工厂模式比工厂方法模式更为简单和有效。