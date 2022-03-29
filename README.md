# Deeplearning_Net_TestOK

#SSD https://github.com/lufficc/SSD

1=代码
&ensp;https://github.com/lufficc/SSD

2=自定义修改  
1=cfg定义  
‘configs\mobilenet_v3_ssd320_voc0712.yaml’  
NUM_CLASSES: 6 #修改==1==类别数+1（背景）  
BACKBONE:  
    NAME: 'mobilenet_v3'  
    OUT_CHANNELS: (112, 960, 512, 256, 256, 64)  
    PRETRAINED: False  #修改==2==不要预训练  
DATASETS:  
    TRAIN: ("voc_2007_train", ) #修改==3==数据集txtname  
    TEST: ("voc_2007_test", )   
1-0==预训练权重是否使用  
‘\ssd\config\defaults.py’   
_C.MODEL.BACKBONE.PRETRAINED = True  
对于‘configs\mobilenet_v3_ssd320_voc0712.yaml’  
BACKBONE:  
    NAME: 'mobilenet_v3'  
    OUT_CHANNELS: (112, 960, 512, 256, 256, 64)  
    PRETRAINED: False  #修改==2==不要预训练  

2==ssd\data\datasets\voc.py   
class_names = ( '__background__', "no", "owf", "of", "fcc", "ob" )  
 #类别小写  
同时：‘configs\mobilenet_v3_ssd320_voc0712.yaml’  
NUM_CLASSES: 6 #修改==1==类别数+1（背景）  

3==dataset路径自定义  
外置文件夹到外面dataset  
F:\F_Test_Vscode_Three\SSD-master\ssd\config\path_catlog.py  
DATA_DIR = '..\datasets\VOCdevkit'     # 外路径'..\datasets\VOCdevkit\VOC2007'  

4==Please upgrade torchvision to 0.3.0+  
F:\F_Test_Vscode_Three\SSD-master\ssd\utils\nms.py  
去掉torchvision版本检查 #7~11  
_nms = torchvision.ops.nms  

5==训练自定义出现loss为nan值问题  
‘configs\vgg_ssd512_voc0712.yaml’  
修改LR=1e-4  

