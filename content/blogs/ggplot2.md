---
author: Thawatchai
date: "2022-10-01T22:41:10+05:30"
description: ""
draft: false
github_link: https://github.com/gurusabarish/hugo-profile
image: /images/projects/GGPLOT.jpg
tags:
- ggplot2
- graph
- example
title: ggplot2
toc: null
---
 กราฟแสดงการเปรียบเทียบร้อยละของรูปแบบการนำเสนอข้อมูล จำแนกตามประเภทของเพจ

## ข้อมูลที่ใช้
ข้อมูลที่ใช้ในการสร้างแผนภาพ เป็นข้อมูลแสดงความสัมพันธ์ระหว่างประเภทของเพจและรูปแบบการนำเสนอข้อมูลเชิงรูปภาพ   [คลิ้กที่นี่](https://docs.google.com/spreadsheets/d/1w1ILx8xsJ8dA93M5JygErvY3-jk5UlXm/edit#gid=723828935)
    
## Syntax ggplot
```{r cars}
install.packages("ggplot2")
library(ggplot2)
library(dplyr)
library(gridExtra)

dat<-read.csv("\\Users\\ACER\\Desktop\\รวมงาน\\ป.โท\\1-65\\data vis\\week4\\dat_vis.csv")
class(dat)

type_levels<-unique(dat$Graph)[order(dat[dat$Name == "general","Per"])]
dat$Graph2<-factor(dat$Graph, levels = type_levels)


g1 <- dat %>%ggplot(aes(x=Graph2,y=Per, fill =Name)) +
  geom_col(position="dodge") + 
  coord_flip() + 
  labs(x="Graph type", y="Percentage")+
  scale_y_continuous(labels = scales::percent)+
  scale_fill_manual(values=c("#F5FF90",
                             "#C490D1"))
```
## แผนภาพ
&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;![image name](/images/projects/gg.png)