# 第 42 卷 第 23 期/2022 年 12 月/光学学报

## sec:preamble preamble
_Pages 1-1_

第 42 卷 第 23 期/2022 年 12 月/光学学报
2334001-1
研究论文
上海同步辐射光源纳米三维成像线站设计、研发及
调试
陶芬
1， 张玲
1， 苏博
2，3， 高若阳
2，3， 杜国浩
1， 邓彪
1，2，3*， 谢红兰
1， 肖体乔
1中国科学院上海高等研究院上海光源科学中心，上海 201204；
2中国科学院上海应用物理研究所，上海 201800；
3中国科学院大学，北京 100049

## sec:section 摘要
_Pages 1-1_

全场透射X 射线显微镜（TXM）具有纳米量级空间分辨、原位、无损和三维（3D）成像等优点，目前已被广泛应用到
多个研究领域中。纳米三维成像线站是上海同步辐射光源（SSRF）二期工程建设内容之一，该线站瞄准前沿领域中的科
学问题和国家战略需求，主要实验方法为TXM 和纳米计算机断层扫描（CT），能量范围为5~14 keV，空间分辨率的设计
指标为20 nm。该线站基于弯铁光源，光束线采用柱面准直镜、双晶单色器和超环面聚焦镜设计方案。实验线站采用自
主设计、整体集成的全场TXM 系统，实验站中单毛细管聚焦元件、TXM 机械系统、纳米CT 控制及数据采集软件均为自
主研发。2021 年SSRF 纳米三维成像线站（BL18B）完成了带光调试与性能测试，实现了20 nm 分辨率的TXM 成像，是国
际上首条基于弯铁光源并实现20 nm 分辨率成像的光束线站，测试结果全部达到线站设计指标，2022 年该线站将对用户
开放使用。
关键词
X 射线光学；透射X 射线显微镜；同步辐射；单毛细管聚焦镜；自主研发
中图分类号
O434. 11
文献标志码
DOI： 10.3788/AOS202242.2334001
Design, Development and Commissioning of 3D Nano Image Beamline at
Shanghai Synchrotron Radiation Facility
Tao Fen
1, Zhang Ling
1, Su Bo
2,3, Gao Ruoyang
2,3, Du Guohao
1, Deng Biao
1,2,3*,
Xie Honglan
1, Xiao Tiqiao
1Shanghai Synchrotron Radiation Facility, Shanghai Advanced Research Institute, Chinese Academy of Sciences,
Shanghai 201204, China;
2Shanghai Institute of Applied Physics, Chinese Academy of Sciences, Shanghai 201800, China;
3University of Chinese Academy of Sciences, Beijing 100049, China

## sec:abstract Abstract
_Pages 1-2_

Full-field transmission X-ray microscope (TXM) has been widely applied in many research fields owing to its
various strengths, such as in-suit non-destructive three-dimensional (3D) imaging with a nanoscale spatial resolution. 3D
nano image beamline, a part of the Shanghai Synchrotron Radiation Facility (SSRF) phase-II project, focuses on cutting-
edge scientific problems and national strategic needs. The main experimental methods are TXM and nano-computed
tomography (nano-CT), and the energy range is 5-14 keV. The design goal for spatial resolution is 20 nm. Based on a
bending magnet source, the beamline is built with a cylindrical collimating mirror, a double crystal monochromator, and a
toroidal condenser. The experimental endstation adopts a self-designed and integrated full-field TXM system, and the
mono-capillary condenser, the TXM mechanical system, and the nano-CT control and data acquisition software of the
experimental endstation are all developed independently. The commissioning and performance tests of the SSRF 3D nano
image beamline (BL18B) have been completed in 2021, with a resolution of 20 nm achieved for TXM imaging. This
beamline is the first TXM beamline based on a bending magnet source in the world with a 20 nm imaging resolution. All
the test results have reached the design goals for this beamline, and it will open to users in 2022.
收稿日期：2022-03-29；修回日期：2022-05-08；录用日期：2022-06-04
基金项目：国家重点基础研究发展计划（2021YFA1600703，2021YFF0601203）、国家自然科学基金大装置联合基金重点项目
（U1932205）
通信作者：
*dengbiao@zjlab. org. cn
2334001-2
研究论文
第 42 卷 第 23 期/2022 年 12 月/光学学报
Key words
X-ray optics; transmission X-ray microscope; synchrotron radiation; mono-capillary condenser; independent
design

## sec:section-2 1 引 言
_Pages 2-4_

随着同步辐射光源和X 射线成像光学元件的发
展，X 射线显微成像技术得到了进一步发展
［1-3］。例如，
在空间分辨率方面，硬X 射线波段的同步辐射纳米成
像已经实现了20 nm 空间分辨率的成像。同步辐射纳
米成像方法的主要技术方案包括全场透射X 射线显微
镜（TXM）成像
［4］、纳米探针扫描成像和纳米分辨相干
衍射成像。TXM 具有很多独特的优点：1）穿透性强，
能够对厚样品进行高分辨无损的三维成像；2）成像方
法多样，如吸收、散射和相位等都可以用来成像，特别
是X 射线相位衬度成像，更适合对轻元素组成的样品
进行成像
［5-6］。目前国际上许多同步辐射装置建有专
用的硬X 射线TXM 线站，例如：NSLS-II 的18ID、
SSRL 的BL6-2C、PLS-II 的7C XNI 和DESY Petra III
的P05 等。另外，部分线站兼具TXM 功能，例如：
ESRF 的ID21、Spring-8 的BL47XU、APS 的26ID-C
与32ID-C 和SLS 的TOMCAT 等
［7-8］。国内北京同步
辐射装置（BSRF）已建成30 nm 空间分辨率的TXM
装置，北京高能同步辐射（HEPS）正在建设专用TXM
线站
［9］。
上海同步辐射光源（SSRF）纳米三维成像线站将
瞄准纳米材料
［10-11］、生命科学
［12］、新能源
［13-14］和新一代
信息技术等领域中的前沿科学问题和国家战略需求，
发挥该线站纳米分辨三维结构表征技术的优势，为相
关学科领域提供先进的纳米结构表征实验平台。
上海同步辐射光源纳米三维成像线站使用弯铁光
源，光子能量覆盖5~14 keV。实验站基于全场透射模
式，可实现20 nm 空间分辨率的成像，满足线站科学目
标的需求。主要实验方法包括TXM、纳米计算机断层
扫描（CT）等，其中：TXM 可将二维空间分辨率提高到
20 nm；纳米CT 可实现样品纳米尺度三维结构的无损
表征。除了可实现以上的实验方法外，还具备TXM、
纳米CT 与X 射线荧光分析（XRF）、X 射线吸收近边
结构（XANES）等方法结合的潜能，可获得样品成分、
化学态等在纳米尺度上的空间信息。
2 光束线设计
纳米三维成像线站光束线从上海同步辐射光源的
18B 单元引出，光束线主要包括柱面准直镜（M1）、双
晶单色器（DCM）、超环面聚焦镜（M2）、狭缝（S1/S2）、
荧光靶、X 光位置探测器（XBPM）和铍窗等。纳米三
维成像光束线光学设计的总体依据是满足全场纳米成
像对相空间的需求，主要从高通量、高次谐波抑制，以
及与实验站椭球镜的匹配效率等方面考虑，采用双晶
单色器、超环面聚焦镜、单毛细管椭球聚焦镜的设计方
案。主要光学元件准直镜、双晶单色器和超环面聚焦
镜分别位于光束线20. 2、23、26 m 处，超环面聚焦镜的
理论焦点位置在39 m 处，在此处设置精密四刀狭缝以
调整入射到波带片全场成像系统中的X 射线光束。光
束线主要光学元件布局及设计光路如图1 所示，其中
BM 为弯铁光源，CCD 为电荷耦合器件。
2. 1 性能指标
纳米三维成像线站的设计目标是满足光束线站应
用目标对光束线性能的要求，包括4 个主要性能参数：
成像空间分辨率、样品处的光子通量、光子能量范围和
能量分辨率。各个参数的主要指标如下。
1） 成像空间分辨率
空间分辨率是本光束线的标志性技术指标，本线
站选择波带片作为成像光学元件，成像分辨率的设计
指标为20 nm。
2） 样品处的光子通量
更高的光子通量意味着更高的探测灵敏度和更短
的测量时间，故高通量是本光束线设计的一个重要
目标。
3） 能量范围
本线站的科学目标是纳米材料结构研究，故选用
硬X 射线波段。根据目前波带片的加工工艺，其在
14 keV 能量以上效率较低，故将能谱上限定为
14 keV。鉴于本光束线的样品是置于空气中的，故将
能谱下限定为5 keV，即能量范围为5~14 keV。
4） 能量分辨率
波带片成像系统要求入射光的单色性满足要求，
对于环带数为2000 的波带片，要求入射光的单色性优
于5×10
-4@8 keV，故能量分辨率需要达到此要求。
上海同步辐射光源纳米三维成像光束线站设计指
标如表1 所示。
2. 2 光束线模拟分析
本线站采用光线追迹软件SHADOW 对光束线性
能进行了模拟分析，计算分析了样品处光斑的通量、光
斑尺寸、能量分辨率、主要部件的传输特性和热负载分
布。计算中考虑了反射镜面形误差、单色器第一晶体
的变形等因素。
图1 纳米三维成像光束线总体布局示意图
Fig. 1 Overall layout of 3D nano image beamline at SSRF
2334001-3
研究论文
第 42 卷 第 23 期/2022 年 12 月/光学学报
1） 光通量分析
光通量分析主要需要考虑光束线的传输效率，主
要包括：几何效率、光学元件的反射率、束线与实验站
的匹配效率、铍窗的吸收和空气的衰减。在入射光张
角为0. 4 mrad×0. 22 mrad 的条件下，几何效率的损失
主要由柱面准直镜、超环面聚焦镜和实验站旋转椭球
聚焦镜等光学元件产生。束线与实验站的匹配效率主
要是指次级光源点与实验站旋转椭球聚焦镜之间的数
值孔径匹配接收效率。XOP 计算得到8 keV 能量时弯
铁光源通量的理论值为5. 7×10
12 photon/s（0. 1% 带
宽下）0. 1%BW。受到光束线传输效率的影响，计算
得到的次级光源点的光通量约为2. 6×10
11 photon/s。
2） 光源点尺寸和发散角
SHADOW 追迹得到8 keV 能量时弯铁光源点的
光斑尺寸［半峰全宽（FWHM）］约为171 μm×54 μm，
发散角约为0. 4 mrad×0. 22 mrad。考虑到单色器热形
变（小于5 mrad）和镜子面形误差（子午方向小于
0. 8 mrad，弧矢方向小于5 mrad），SHADOW 追迹得到
8 keV 能量时次级光源点的光斑尺寸（半峰全宽）约为
86 μm×134 μm，发散角约为0. 73 mrad×0. 30 mrad。
3） 能量分辨率
由SHADOW 模拟计算得到8 keV 能量时，
Si（111）双平晶单色器的能量分辨率为1. 3×10
-4。
4） 关键光学元件热分析和热负载分析
准直镜水平放置，高温集中在光斑中心处，最高温
度为30. 3
oC，最大热应力为18. 6 kPa，热功率引起镜
子中心的最大变形量为12. 3 μm，利用水冷较好地控
制了准直镜温度的升高，很好地控制了面形误差，达到
了提出的要求。单色器晶体热变形会影响聚焦光斑的
形状，从而影响样品点的光通量，为此要求热负载引起
的单色器晶体形变尽量小，此时单色器最高温度为
36. 7
oC，最大热应力为0. 4 MPa，最大变形量为
0. 84 μm，通过水冷后一晶的形变得到了有效控制，达
到了所需要求。
3 实验站设计
纳米三维成像线实验站将开展TXM 和纳米CT
等实验。实验站还具备发展TXM 与XANES 等方法
结合的潜能，可获得样品三维结构、成分和化学态等在
纳米尺度上的空间信息。参照国际纳米CT 实验站配
置和发展趋势，纳米CT 实验站配有单毛细管椭球聚
焦镜、针孔、样品台、波带片、相移环和成像CCD 等关
键元件。纳米三维成像实验站原理图，如图2 所示。
纳米成像系统及其关键聚焦元件椭球镜一直被国
外公司垄断，器件价格昂贵，且技术支持和维护费用也
很高。为实现纳米成像系统的自主研发，经过4 年多
的联合攻关，成功攻克了毛细管拉制成型工艺控制、参
数精密检测和成品率低等技术难题，2019 年成功实现
了单毛细管椭球镜的研制。在此基础上，上海同步辐
射光源同时解决了高稳定机械系统设计与集成、精密
运动控制与数据采集等一系列技术难题，自主研发了
国内首套专用纳米CT 系统。
3. 1 单毛细管椭球聚焦镜
椭球聚焦镜是一种反射面为椭球的单毛细管，是
纳米全场成像的核心部件，具有两个功能：其一，将次
级光源点的X 射线会聚到样品点处，以提高样品点处
的光通量密度；其二，根据成像的系统要求，聚焦镜出
射光的数值孔径应与波带片环状照明的数值孔径一
致。椭球镜具有传输效率高、像差小、能提供TXM 所
需的均匀照明视场等特点，TXM 装置大多采用它作为
聚焦元件。上海同步辐射光源二期纳米三维成像线站
采用弯铁光源，为提高成像效率，椭球聚焦镜是TXM
装置聚焦的最佳选择。
图3 是椭球聚焦镜的光学原理示意图。X 射线次
级光源点处于椭球的一个焦点F 处，掠入射照射到旋
转椭球聚焦镜表面上，经表面全反射后聚焦在旋转椭
球镜的另一焦点F'处（样品点处）。在光轴上放置光
阑，形成照明样品的空心聚焦光锥，聚焦后形成环状光
表1 上海同步辐射光源纳米三维成像光束线站设计指标
Table1 Design goals of 3D nano image beamline at SSRF
Component
Beamline
Endstation
Index
Energy range /keV
Energy resolution @8 keV
Photon flux at sample@8 keV@300 mA /（photon·s
-1）
Spatial resolution@8 keV（TXM） /nm
Value
5-14
5. 0×10
5×10
图2 纳米三维成像实验站原理图
Fig. 2 Schematic diagram of 3D nano image beamline endstation at SSRF
2334001-4
研究论文
第 42 卷 第 23 期/2022 年 12 月/光学学报
斑照射在波带片上
［15］。
根据上海同步辐射光源二期纳米成像光束线站的
参数，设计椭球聚焦镜的参数如表2 所示。
3. 2 波带片
波带片是X 射线“透镜”的一种，利用Au 或者Ni
刻蚀来挡住偶（奇）数半波带，进而可实现透过奇（偶）
数级波带的光场的相干相长。波带片在纳米成像中作
为物镜实现放大成像，将纳米尺度信息放大到微米量
级，然后用具有微米分辨率的X 射线探测器进行成像。
在平行光入射的条件下，根据瑞利判据对空间分辨率
的定义和光栅一级衍射原理，可求出波带片最外环宽
度Δr 和空间分辨率δ 之间的关系为
δ = 1. 22 ⋅Δr。
（1）
由于X 射线穿透性强、相互作用弱，故与透射光相
比，衍射光太弱。此时，若采用正入射的照明方式，连
续穿过样品和波带片的透射光将会直接到达探测器，
进而引起成像本底过高，信噪比太低。斜入射不但可
以避免这一现象，而且可以将波带片的空间分辨率提
高一倍。对于TXM 系统，椭球聚焦镜产生的空心光
锥照明波带片采用了斜入射的方式，可以将波带片的
空间分辨率提高一倍
［16］，即
δ = 0. 61 ⋅Δr。
（2）
上海同步辐射光源纳米成像线站采用Applied
Nanotools 公司制备的波带片作为放大光学元件，波带
片的最外环宽度为25 nm，直径为125 μm。
4 线站调试
纳米三维成像线站于2016 年11 月开始建设，经过
5 年的努力，完成了光束线的安装、准直与调试，并于
2021 年12 月进行了线站的光束线与实验站的调试。
上海同步辐射光源纳米三维成像线站（BL18B）装置图
如图4 所示。
纳米三维成像线站主要调试与测试的指标为能量
范围、能量分辨率、样品处光通量和空间分辨率等参
数。下面介绍线站各个参数的调试方法和结果。
4. 1 能量范围
为了确定单色器出光能量的范围准确性，通过选
择Ti 元素的K 边（能量为4. 966 keV）与Au 元素的L1
（能量为14. 353 keV）边吸收谱来确定单色器的能量
是否可以达到设计范围。使用高纯度的Ti 和Au 金属
标准箔片、气体电离室和电子学系统进行检测。将元
素吸收片放置在两个电离室的中间，通过电流表读数
来观察采集元素的吸收边。
两种元素的X 射线吸收近边结构(XANES)谱测
试结果如图5 所示。Ti 元素的K 吸收边能量理论值为
4966. 4 eV，测得的Ti 元素的K 边吸收谱如图5（a）所
图3 旋转椭球聚焦镜原理示意图
［15］
Fig. 3 Schematic diagram of rotating ellipsoidal capillary
[15]
表2 椭球聚焦镜的物理参数
Table 2 Parameter of ellipsoidal capillary

## sec:model Model
_Pages 4-6_

ABS25-8
Length of
ellipsoidal
capillary L /mm
Entry radius
H /μm
Exit radius
h /μm
Semi major
axis a /mm
Semi minor
axis b /mm
0. 524
Working
distance W /
Maximum
accepted
divergence of
capillary φ2 /mrad
6. 2
图4 上海同步辐射光源自主研制的TXM 系统
Fig. 4 TXM system independently developed by SSRF
2334001-5
研究论文
第 42 卷 第 23 期/2022 年 12 月/光学学报
示，其中I1 为电离室1 的计数,I2 为电离室2 的计数。
Au 元素的L1 吸收边的能量理论值为14352. 8 eV，测
得的Au 元素的L1 边吸收谱如图5（b）所示。因此，测
得的单色光能量范围为5~14 keV，满足线站的设计与
验收指标。
4. 2 能量分辨率
在固定能量下，利用双晶单色器二晶的Pitch2 角
度调节得到摇摆曲线，将摇摆曲线的半峰全宽作为该
能量下的能量分辨率。使用气体电离室和电子学系统
测量单色器二晶的摇摆曲线，重复测量三次，取平均值
作为该能量下的能量分辨率，此时白光狭缝开口大小
为8. 0 mm×4. 4 mm，单色光狭缝开口大小为
8. 0 mm×8. 0 mm。能量分辨率的计算公式为
E = (
Δδs
2 + (
Δδd
2 ⋅cot θ ≈Δθ ⋅cot θ，（3）
式中：ΔE 为能量变化量；E 为X 射线光子能量；Δδs 为
入射光束的垂直发散角；Δδd 为晶体的Darwin 宽度；θ
为布拉格角；Δθ 为摇摆曲线的半峰全宽。
三次测试数据如表3 所示，摇摆曲线如图6 所示，
其半峰全宽分别为46. 92、46. 92、46. 35 μrad，计算得
到8 keV 能量下的能量分辨率平均值为1. 83×10
-4。
4. 3 样品处光通量
由于上海同步辐射光源正常运行的电流强度为
200~260 mA，实验测试时储存环运行的电流强度为
200 mA，故测量完成后需将数值换算成300 mA 下的
数值以与设计指标进行对比。测量方法是在8 keV 能
量下，将电离室放置于样品点处，通过检测样品点处电
离室的电流表计数，综合考虑空气吸收等因素后推算
得到300 mA 下样品点的光通量密度。使用电离室和
电子学系统将入射光能量调节至8 keV，此时电流强
度为200 mA，白光狭缝大小为8. 0 mm×4. 4 mm，单
色光狭缝大小为8. 0 mm×8. 0 mm。电离室中充斥着
空气，电离室电极长度为10 mm，高压为800 V。用电
离室进行测量，8 keV 能量下光子通量的计算公式为
N = I0ε0
eEη，
（4）
式中：N 为光子通量；I0 为电离室的电流；ε0 为工作气体
的平均电离能（空气的平均电离能为34. 4 eV）；e 为电
子电荷量；η 为电离室的效率，其表达式为
图5 XANES 谱线。
（a） Ti 元素标准样品K 边XANES 谱测试曲线；
（b） Au 元素标准样品L1 边XANES 谱测试曲线
Fig. 5 XANES spectra. (a) XANES spectrum of Ti K-edge; (b) XANES spectrum of Au L1-edge
表3 能量分辨率三次测试结果
Table 3 Three test results of energy resolution
Test No.
Peak position /μrad
188. 64
187. 81
187. 81
FWHM /μrad
46. 92
46. 92
46. 35
Energy resolution
1. 84×10
1. 84×10
1. 82×10
Average of
ΔE/E
（1. 83±0. 01）×10
图6 8 keV 能量处摇摆曲线的三次测量结果
Fig. 6 Three test results of rocking curve at energy of 8 keV
2334001-6
研究论文
第 42 卷 第 23 期/2022 年 12 月/光学学报
η = 1 - exp( - μx)，
（5）
式中：μ 为吸收系数；x 为电离室中两个电极间的距离。
实验时样品处电离室中的电流读数为4. 8×
-9 A，X 光在空气中的线性吸收系数μ 约为
0. 01188 cm
-1。200 mA 束流时的光子通量N1为
N 1 =
I0ε0
eE[
1 - exp(
-μx
4. 8 × 10
-9 × 34. 4
1. 6 × 10
-19 × 8000 ×[
1 - exp(
-0. 01188 × 1
= 1. 09 × 10
10 photon ⋅s
-1，（6）
300 mA 束流时的光子通量N2为
N 2 = (300 I) ⋅N 1，
（7）
式中：I 为测试时的电流强度。N1换算到300 mA 电流
强度下的光通量的值为N 2=1. 64×10
10 photon/s@
8 keV。
4. 4 空间分辨率
使用分辨率靶作为样品，放置在TXM 系统的样
品处，通过观察星条靶靶线测试系统的空间分辨率。
标准分辨率测试卡（Carl Zeiss AG，X30-30-2）的最小
尺寸为30 nm。将单色器能量设置为8 keV，样品处放
置X 射线分辨率测试卡，调节TXM 成像系统中各元
件的距离和姿态，对分辨率靶进行成像，利用功率谱
（PSD）对成像结果进行分析，即对图片进行二维傅里
叶变换后，对固定径向频率处方位角（沿圆周）的二维
功率谱强度进行积分，得到成像空间分辨率
［17］。
星条靶测试结果如图7 所示。图7（a）为曝光时间
为60 s 时的星条靶成像结果。测试结果显示，相邻明
暗条纹间距为30 nm 的靶线能被清晰分辨。图7（b）为
功率谱分析曲线，截距的空间频率为25. 5 μm
-1，计算
后得到的空间分辨率为19. 6 nm。
上海同步辐射光源纳米三维成像线站基于自主研
制的单毛细管聚焦元件、TXM 机械系统、纳米CT 控
制及数据采集软件，完成了能量范围、能量分辨率、样
品处光通量和空间分辨率等设计指标的检测。单色光
能量实际检测范围为5~14 keV，达到设计要求。
8 keV 实际能量分辨率为1. 83×10
-4，优于设计的分辨
率（5. 0×10
-4）。实际样品处光通量为1. 64×
10 photon/s@8 keV，高于设计值（5×10
9 photon/s@
8 keV）。实际空间分辨率为19. 6 nm，高于设计的
20 nm 空间分辨率。各项指标的实际测量结果均达到
或优于理论设计指标。

## sec:section-3 5 结 论
_Pages 6-6_

上海同步辐射光源纳米三维成像光束线站各项指
标的实测值均达到并部分优于设计指标，是国际上首
条基于弯铁光源并实现20 nm 分辨率成像的光束
线站。
上海同步辐射光源纳米三维成像线站主要实验方
法为TXM 和纳米CT，具有三维成像分析的优势。同
时，TXM、纳米CT 与XRF、XANES 方法进行结合，具
有元素分析优势。该线站于2022 年对用户开放使用，
其成像技术将会被应用到更加广阔的科研领域中，并
推动相关科研工作的进步。

## sec:section-4 致谢
_Pages 6-7_

该光束线安装和调试过程得到了上海同步辐射
光源束线工程部和其他同事的大力支持，在此表示感
谢。同时，感谢上海科技大学佟亚军博士的倾力支持。
参
考
文
献
[1]
李凡, 康乐, 杨福桂, 等. 基于X 射线近场散斑的波前
检测技术研究现状[J]. 光学学报, 2022, 42(8): 0800002.
Li F, Kang L, Yang F G, et al. Present research status
of X-ray near-field speckle based wavefront metrology[J].
Acta Optica Sinica, 2022, 42(8): 0800002.
[2]
杨霞, 李俊琴, 曹杰峰, 等. 基于同步辐射的时间分辨
X 射线铁磁共振方法[J]. 光学学报, 2021, 41(15):
1534002.
Yang X, Li J Q, Cao J F, et al. Time-resolved X-ray
ferromagnetic resonance method based on synchrotron
radiation[J]. Acta Optica Sinica, 2021, 41(15): 1534002.
[3]
骆钧尧, 郭智, 黄浩, 等. 多层膜光栅衍射效率的同步
图7 星条靶成像结果和功率谱分析曲线。
（a）星条靶成像图；
（b）功率谱分析曲线
Fig. 7 Image result and power spectral density curve of start bar. (a) Image result of start bar; (b) power spectral density curve
2334001-7
研究论文
第 42 卷 第 23 期/2022 年 12 月/光学学报
辐射研究[J]. 光学学报, 2021, 41(14): 1405001.
Luo J Y, Guo Z, Huang H, et al. Synchrotron radiation
research on diffraction efficiency of multilayer coated
grating[J]. Acta Optica Sinica, 2021, 41(14): 1405001.
[4]
Chen-Wiegart Y C K, Cronin J S, Yuan Q X, et al. 3D
non-destructive morphological analysis of a solid oxide
fuel cell anode using full-field X-ray nano-tomography[J].
Journal of Power Sources, 2012, 218: 348-351.
[5]
Chen T Y, Chen Y T, Wang C L, et al. Full-field
microimaging with 8 keV X-rays achieves a spatial
resolutions better than 20 nm[J]. Optics Express, 2011,
19(21): 19919-19924.
[6]
Li W J, Wang N, Chen J, et al. Quantitative study of
interior nanostructure in hollow zinc oxide particles on the
basis
nondestructive
X-ray
nanotomography[J].
Applied Physics Letters, 2009, 95(5): 053108.
[7]
Liu X Y, Ronne A, Yu L C, et al. Formation of three-
dimensional bicontinuous structures via molten salt
dealloying studied in real-time by in situ synchrotron X-
ray nano-tomography[J]. Nature Communications, 2021,
12: 3441.
[8]
Andrews J C, Pianetta P, Meirer F, et al. Hard X-ray
full field nano-imaging of bone and nanowires at SSRL
[C]. AIP Conference Proceedings, 2010, 1234: 79-82.
[9]
袁清习, 黄万霞, 洪友丽, 等. BSRF-4W1A 纳米成像光
束线调试[J]. 核技术, 2010, 33(10): 721-724.
Yuan Q X, Huang W X, Hong Y L, et al. Adjustment
and test of the nano-imaging beamline at BSRF[J].
Nuclear Techniques, 2010, 33(10): 721-724.
[10]
Weker J N, Liu N, Misra S, et al. In situ
nanotomography
and
operando
transmission
X-ray
microscopy of micron-sized Ge particles[J]. Energy &
Environmental Science, 2014, 7(8): 2771-2777.
[11]
Nelson J, Misra S, Yang Y, et al. In operando X-ray
diffraction and transmission X-ray microscopy of lithium
sulfur batteries[J]. Journal of the American Chemical
Society, 2012, 134(14): 6337-6343.
[12]
Wang S X, Wang D J, Wu Q, et al. 3D imaging of a rice
pollen grain using transmission X-ray microscopy[J].
Journal of Synchrotron Radiation, 2015, 22(4): 1091-
1095.
[13]
安汉文, 莫生凯, 李梦璐, 等. 同步辐射多模态成像技
术在储能电池领域的研究进展[J]. 储能科学与技术,
2022, 11(3): 834-851.
An H W, Mo S K, Li M L, et al. Research progress of
synchrotron radiation multimodal imaging technology in
field of energy storage batteries[J]. Energy Storage
Science and Technology, 2022, 11(3): 834-851.
[14]
Yang Y, Xu Z R, Steiner J D, et al. Quantitative
probing of the fast particle motion during the solidification
of battery electrodes[J]. Applied Physics Letters, 2020,
116(8): 081904.
[15]
陶芬, 王玉丹, 任玉琦, 等. X 射线纳米成像单毛细管
椭球镜的设计与检测[J]. 光学学报, 2017, 37(10):
1034002.
Tao F, Wang Y D, Ren Y Q, et al. Design and
detection of ellipsoidal mono-capillary for X-ray nano-
imaging[J]. Acta Optica Sinica, 2017, 37(10): 1034002.
[16]
洪友丽. X 射线相衬显微成像方法研究及其应用[D]. 北
京: 中国科学院大学, 2012.
Hong Y L. X-ray phase contrast imaging research and
application in X-ray microscopy[D]. Beijing: University of
Chinese Academy of Sciences, 2012.
[17]
Ge M Y, Coburn D S, Nazaretski E, et al. One-minute
nano-tomography using hard X-ray full-field transmission
microscope[J]. Applied Physics Letters, 2018, 113(8):
083109.
