---
title: Oracle数据库最大打开游标阈值
seo-title: Oracle数据库最大打开游标阈值
description: 了解如何为打开的游标配置最大值Oracle。
seo-description: 了解如何为打开的游标配置最大值Oracle。
uuid: c1d20997-f853-4772-b1c6-8cea73221d0a
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/maintaining_the_aem_forms_database
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: d3565776-1b7d-498c-9840-b17f80170d9b
exl-id: ad14ff27-964f-481f-a8ef-052d9cfb7734
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '101'
ht-degree: 0%

---

# Oracle数据库最大打开游标阈值{#oracle-database-maximum-open-cursors-threshold}

要为Oracle中打开的游标配置最大值，您可能需要将此值调整为与应用程序相适的数字。 显然，在中等负载下，打开的游标数平均为2700。 建议您以3000的上限开始。 有关更多信息，请转到[https://www.orafaq.com/node/758](https://www.orafaq.com/node/758)。
