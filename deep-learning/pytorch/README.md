

# 预处理
transform.Resize((256))  
transform.Resize((256,256))  
两者的区别：  
假如是（512,1024）的图片，Resize((256))会变为（256,512）的图片，Resize((256,256)) 会变为（256,256）
Resize((256))之后，需要CenterCrop或RandomCrop来裁剪
