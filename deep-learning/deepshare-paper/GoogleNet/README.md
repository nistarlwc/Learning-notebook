# GoogleNet - inception

## 多尺度卷积


## 1x1卷积


## GAP，global average pooling
在[AlexNet](../AlexNet/README.md)中已有说明  
用GAP替代FC全连接层。有两个优点：  
一是GAP在特征图与最终的分类间转换更加简单自然；  
二是不像FC层需要大量训练调优的参数，降低了空间参数会使模型更加健壮，抗过拟合效果更佳。  