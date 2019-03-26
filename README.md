**工厂模式：**我只要面包，你从哪里来我管不着。

**单例模式：**我的存款，就那么多，不是风刮来的，用的多，省的少。

**原型模式：**多利（克隆羊)，同样的DNA但是不是同一个。

**代理模式：**经纪人，签约人的大部分事务，有我接手。

**委派模式：**国外的程序员高价谈来的项目，转手外包给中国的程序猿，不用干活，钱照样拿。

**策略模式：**娃娃机的娃娃，想要哪个你自己挑

**模板模式：**流水线工厂，一步步来，一步不能少，特定岗位，特殊要求。

**适配器模式：**转换插头。

**装饰器模式：**逛街出门前的女生（画2小时的装）。

**观察者模式：**买彩票（中奖通知）



### AOP的代码片段

![1553584848110](https://github.com/yongahua/design-pattern-summarize/blob/master/1553584848110.png)

<aop:config >
	<aop:pointcut id="transactionPointcut"
					  expression="execution(* com.pintang.service..*Impl.*(..))" />
	<aop:advisor pointcut-ref="transactionPointcut"
					 advice-ref="transactionAdvice" />
</aop:config >
<aop:config proxy-target-class="true"></aop:config >



package com.pintang.service.impl;

import java.util.List;

import org.apache.log4j.Logger;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.stereotype.Service;

import com.pintang.dao.BannerTopMapper;
import com.pintang.model.BannerTop;
import com.pintang.service.BannerTopService;

@Service
public class BannerTopServiceImpl implements BannerTopService{

		private static Logger logger = Logger.getLogger(BannerTopServiceImpl.class);
	
		@Autowired
		private BannerTopMapper bannerTopMapper;
		
		@Override
		public Integer insert(BannerTop bannerTop) {
			logger.info("begin insert");
			return bannerTopMapper.insert(bannerTop);
		}
	}
### IOC的代码片段：

```
<beans>
    <import resource=”resource1.xml” />
    <bean id=”bean1” class=”com.test.bean.Bean1”></bean>
    <bean name=”bean2” class=”Brave”></bean>
    <alias alias="bean3" name="bean2" />
    <import resource=”resource2.xml” />
</beans>
```

```
@Test
public void sayHello() {
    BeanFactory beanFactory =
              new ClassPathXmlApplicationContext("Bean1.xml");
    //根据类型获取bean
    Bean1 bean1 = beanFactory.getBean("bean1",Bean1.class);
    bean1.info();
}
```

### DI的代码片段：

<!-- 自动扫描controller包下的所有类，如果@Controller注入为bean -->
    <context:component-scan base-package="com.pintang"/>

![1553586461924](https://github.com/yongahua/design-pattern-summarize/blob/master/1553586461924.png)
