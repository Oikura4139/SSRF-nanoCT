# X射线纳米成像单毛细管椭球镜的设计与检测

## sec:preamble preamble
_Pages 1-1_

第３７卷 第１０期
光 学 学 报
Vol．３７,No．１０
２０１７年１０月
ACTAOPTICASINICA
October,２０１７
X 射线纳米成像单毛细管椭球镜的设计与检测
陶 芬１,２,王玉丹１,任玉琦１,丰丙刚１,佟亚军１,杜国浩１,邓 彪１,２,孙天希３,谢红兰１,肖体乔１
１中国科学院上海应用物理研究所,上海２０１２０４;
２中国科学院大学,北京１０００４９;
３北京师范大学,北京１００８７５
摘要 设计并成功研制了单毛细管椭球镜,并通过光学及X 射线方法测试了它的特性.椭球镜的面形误差为
１５μrad,能量为９keV 时聚焦光斑直径为４０μm,聚焦光斑发射角为１．
７５mrad.基于研制的椭球镜,在上海光源X
射线成像线站搭建X 射线纳米成像系统,并实现了纳米成像,这表明该椭球镜可满足X 射线纳米成像的需求.
关键词 X 射线光学;X 射线显微镜;单毛细管椭球镜;检测;同步辐射
中图分类号 O４３４．
１９ 文献标识码 A
doi:１０．
３７８８/AOS２０１７３７．
收稿日期:２０１７Ｇ０５Ｇ１０;收到修改稿日期:２０１７Ｇ０６Ｇ０５
基金项目:国家自然科学基金(U１５３２１１８,１１７７５２９７,１１４０５２６１)
作者简介:陶 芬(１９９４—),女,硕士研究生,主要从事X射线和光学检测方面的研究.EＧmail:taofen＠sinap．
ac．
导师简介:邓 彪(１９８１—),男,博士,研究员,硕士生导师,主要从事X射线成像及成像光学方面的研究.
EＧmail:dengbiao＠sinap．
ac．
cn(通信联系人)
DesignandDetectionofEllipsoidalMonoＧCapillary
forXＧRayNanoＧImaging
TaoFen
１ ２ WangYudan
１ RenYuqi
１ FengBinggang
TongYajun
１ DuGuohao
１ DengBiao
１ ２ SunTianxi
３ XieHonglan
１ XiaoTiqiao
１ShanghaiInstituteofAppliedPhysics ChineseAcademyofScience Shanghai２０１２０４ China
２UniversityofChineseAcademyofSciences Beijing１０００４９ China
３BeijingNormalUniversity Beijing１００８７５ China
Abstract AnellipsoidalmonoＧcapillaryisdesignedandfabricated anditsperformanceismeasuredbybothoptical
measurementandXＧraytesting敭TheprofileerrorsoftheellipsoidalmonoＧcapillaryis１５μrad敭Thediameterof
focusingspotis４０μm andthelaunchingangleoffocusingspotis１敭７５mradatenergyof９keV敭Basedthe
developedellipsoidalmonoＧcapillary aXＧraynanoＧimagingsystemisdesignedandconstructedattheXＧrayimaging
beamline BL１３W１ inShanghaisynchrotronradiationfacility SSRF 敭TheXＧraynanoＧimagingisachievedwith
utilizationoftheellipsoidal monoＧcapillary whichindicatesthattheellipsoidal monoＧcapillary can meetthe
requirementofXＧraynanoＧimaging敭
Keywords XＧrayoptics XＧraymicroscope ellipsoidalmonoＧcapillary detection synchrotronradiation
OCIScodes ３４０敭７４６０ ３４０敭７４４０ ３４０敭７４７０

## sec:section １ 引 言
_Pages 1-7_

全场透射X 射线显微镜(TXM)可实现厚样品内部三维结构的成像,世界上许多光源都已建立了硬X
射线TXM 成像系统,如斯坦福同步辐射光源(SSRL)
[１Ｇ２]、国家同步辐射光源(NSLS)、国家同步辐射研究中
心(NSRRC)
[３]和北京同步辐射装置(BSRF)
[４].TXM 系统目前已实现了２０nm 的空间分辨[５],广泛应用
于材料、生物、能源、纳米等诸多科学领域[１,３,６].
TXM 是光学成像显微镜在X 射线波段的发展,它们的成像原理和光路结构基本相同.TXM 以X 射线
(同步辐射或X 光机)作为光源,聚焦镜将X 射线聚焦到样品上,经X 射线透镜(波带片)放大后成像.聚焦
１０３４００２Ｇ１
光 学 学 报
镜是TXM 的核心部件,具有２个功能:１)将次级光源点的X 射线会聚到样品点,以提高样品点处的光通量
密度;２)根据成像系统的要求,聚焦镜出射光的数值孔径应与波带片环状照明的数值孔径一致.目前应用
于全场纳米成像装置上的聚焦镜主要有复合折射透镜[７Ｇ９]、光束整形器[１０Ｇ１１]和椭球聚焦镜[１２Ｇ１３].复合折射透
镜具有立体接收角大的优点,但是它制备困难,效率相对较低,且焦距对能量敏感.光束整形器的衍射效率
低(１％~１０％),且有带宽限制,这限制了它在TXM 成像中的应用.椭球聚焦镜的传输效率高达９０％以上,
具有像差小、体积小、易于调节等特点,还可以提供TXM 所需的均匀照明视场,因此大多数TXM 装置都将
它作为聚焦元件[３].
椭球聚焦镜是反射面为椭球面的单毛细管,如何控制面形误差是研制椭球镜的关键,该技术长期被国外
厂商垄断.上海光源二期拟建设一条纳米三维成像线站,分辨率的设计指标为２０nm.为实现这一设计目
标,实现关键光学元件的国产化,本课题组设计并成功研制了单毛细管椭球镜,并通过光学及X 射线方法对
它的特性进行了测试.基于研制的椭球镜,在上海光源X 射线成像线站搭建X 射线纳米成像系统,并实现
了纳米成像,这表明研制的椭球镜可满足X 射线纳米成像的需求.
２ 椭球镜的物理设计与制备
图１为上海光源X 射线成像线站(BL１３W１)TXM 的示意图.TXM 包括椭球镜、针孔、波带片与探测
器等,空间分辨率设计目标为１００nm＠９keV.根据空间分辨率的要求,选择直径为１００m、最外环宽度为
７０nm 的波带片,能量为９keV 时波带片的焦距为５０．
８mm,数值孔径(NA)为０．
９８mrad.
图１ 上海光源成像线站(BL１３W１)TXM 示意图
Fig敭１ TXMschematicofimagingbeamline BL１３W１ inShanghaiSynchrotronRadiationFacility
椭球镜为全反射元件,反射面为椭球面,图２为椭球镜的光学原理示意图.光源点位于椭圆的焦点F
(当椭球的长半轴a 远大于短半轴b 时,焦点靠近顶点)处,入射光照射到椭球镜表面后在表面发生全反射,
将光源成像在椭球镜的另一个焦点F′(样品)处,再经过光束挡光器后形成环状光斑照射在波带片上,为波
带片提供空心光锥照明.
p１和p２为椭球镜入射光的２个边界线段,对应的q１和q２为出射光的２个边界线段.p１和FF′光轴
的夹角为最大接收角(α１).为了最大限度地接收到光,最大接收角为光束次级光源点垂直发散角的一半.
空心光锥照射到波带片上,形成环状带照明,该区域为R１与R２之间的范围,与此对应的椭球镜的发散角θ
范围为[φ１,φ２]
[１２].
由图２的几何关系可知:
p１＋q１＝２a,
(１)
p１sinα１－q１sinφ１＝０,
(２)
p１cosα１＋q１cosφ１＝２c,
(３)
b＝a
２－c
(４)
式中a 为椭球的长半轴,
b 为短半轴,
c 为半焦距,
α１为椭球镜的接收角,φ１和φ２为反射光与椭球聚焦镜长
轴的夹角[１４].
由于椭球镜的离心率很大,所以用椭球镜的长度L 来代替圆弧的长度,L 的计算公式为
１０３４００２Ｇ２
光 学 学 报
２ 椭球镜的光学原理示意图
Fig敭２ OpticalprincipleschematicofellipsoidalmonoＧcapillary
L ＝q１cosφ１－q２cosφ２.
(５)
由图２可知,工作距离W 、入口半径H 、出口半径h 分别为
W ＝q２cosφ２,
(６)
H ＝q１sinφ１,
(７)
h＝q２sinφ２.
(８)
TXM 成像要求椭球镜出射光的数值孔径与波带片的数值孔径相匹配.根据实践经验[１５],椭球镜提供
的空心光锥约为照明波带片总面积的１/２,即φ１为NA 的７０％~７８％.为实现基于波带片的最高分辨率,
一般要求空心光锥照射到波带片的最外环,即φ２为NA 的９０％~１００％.当φ２＞NA 时,系统的分辨率没
有明显提高,成像衬度下降明显,而且会造成波带片漏光.选择φ１＝０．
７８NA,φ２＝NA＝０．
９８mrad作为设
计依据.上海光源X 射线成像线站的光束是从插入件扭摆器引出的,光源点到样品的距离为３４m
[１６Ｇ１８].由
此可知椭球镜的长半轴a＝１７m,光源点垂直发散角为０．
０１２mrad,即α１＝０．
０１２mrad/２＝０．
００６mrad.设
计的椭球镜参数如表１所示.
表１ 椭球镜的参数
Table１ ParametersofellipsoidalmonoＧcapillary
Parameter
Value
Parameter
Value
XＧrayenergyE /keV
LengthL/mm
１０５．
EntryradiusH /μm
２０２．
SemiＧmajoraxisa/mm
Exitradiush/μm
１５７．
SemiＧminoraxisb/mm
Maximumdivergenceangleoffocusingring２φ２/mrad
WorkingdistanceW /mm
１６０．
Minimumdivergenceangleoffocusingring２φ１/mrad
Maximumacceptanceangle/mrad
为保证椭球镜的面形符合设计要求,综合考虑吸收、材料密度与X 射线全反射临界角的关系,以高密度
硼硅酸盐玻璃管作为母管[１９],基于温度精密可控的玻璃拉丝塔进行拉制,成功研制了一批椭球镜,如图３
所示[１３].
３ 椭球镜的相关检测
１ 光学检测
为分析研制椭球镜的面形误差,采用光学千分尺对椭球镜的外径进行检测,再通过外径推导出内径,从
而实现内径的检测.光学测试采用的是LSＧ７０３０M 型千分尺,可实现±０．
５μm 的测量精度和±０．
０６μm 的
重复精度.测试时扫描间隔为０．
２mm.图４为测试得到的内径曲线与理论椭球面曲线的比较,分析可得到
该椭球镜的面形误差为１５μrad.
２ 同步辐射X射线检测
为实现椭球镜的同步辐射X 射线检测,在上海光源成像线站搭建了椭球镜测试系统.基于同步辐射光
１０３４００２Ｇ３
光 学 学 报
图３ 研制的椭球镜照片
Fig敭３ PictureofdevelopedellipsoidalmonoＧcapillary
图４ 椭球镜的光学测试结果
Fig敭４ OpticaltestingresultforanellipsoidalmonoＧcapillary
和高分辨X 射线成像探测器检测椭球镜的性能,包括聚焦光斑的焦斑尺寸、均匀度及椭球镜后不同位置处
的环带照明光斑尺寸,从而计算发散角.测试原理图如图５所示,光束挡光器放置在椭球镜的前端,探测器
上得到圆环状光斑,此圆环反映了空心锥光束照射位置处的椭球镜的内部形状.如果椭球镜的制造很完美,
那么会产生均匀理想的细圆环.当椭球镜存在面形误差时,圆环就会产生形变.
图５ 椭球镜X 射线测试原理示意图
Fig敭５ PrincipleschematicofXＧraytestingforellipsoidalmonoＧcapillary
测量过程中,通过调节椭球镜的旋转角(w)和俯仰角(v)２个维度方向来调整聚焦光环的形状与光斑均
匀度.首先大范围粗调w 或v 的方向找到聚焦光斑,再小范围细调聚焦光斑的形状及均匀度.
１０３４００２Ｇ４
光 学 学 报
图６是在距离焦点５５cm 和１００cm 处以及在焦点处聚焦光斑的形状及三维光强分布.图６(a)是椭球
镜在距离焦点５５cm 处的近场成像,图６(b)是距离焦点１００cm 处的远场成像,图６(c)是距离聚焦镜出口
１４．
９cm 处,通过测量光斑的半峰全宽(FWHM)得到的４０μm×４０μm 的焦点光斑,焦深为６．
０mm.实际
工作距离为１５５mm,满足椭球镜工作距离约为１６０．
７mm 的设计要求.
图６ 距离焦点(a)５５cm、(b)１００cm 处以及(c)焦点处聚焦光斑的形状及三维光强分布图
Fig敭６ ShapesandthreeＧdimensionallightintensityprofilesoffocusingspotat a ５５cmand
b １００cmfromfocalpointand c atfocalpoint
在距离焦点５５cm 处及向后等间隔S１＝S２＝S３＝S４＝５cm 处,分别测量聚焦圆环的内外环直径,得到
近场聚焦圆环的外环直径D１、D２、D３、D４、D５;在距离焦点１００cm 处及向后等间隔S６＝S７＝１０cm 处,分
别测量聚焦圆环的内外环直径,得到近场聚焦圆环的外环直径D６、D７、D８.
由于发散角只有几毫弧度,比较小,因此可以得到发散角θ 的计算公式为
tan(
θ/２)≈sin(
θ/２)≈θ/２＝Δ
(９)
进而得到发散角θ＝(D１－D２)/S１.因此,可以根据测量点的数据得到不同位置处光斑的尺寸曲线,然后对
其进行拟合处理,将拟合曲线的斜率作为发散角的值.得到的拟合曲线如图７所示.
由图７可知,椭球镜聚焦光斑外环的发散角约为１．
７５mrad,即φ１＝０．
９３５＝０．
９５NA,可与直径为
１００μm、最外环线宽Δr＝７０nm 的波带片匹配.
３ TXM 成像测试
基于研制的椭球镜,在上海光源BL１３W 线站搭建了TXM 实验系统,如图８所示.在图８中,１为椭球
镜,２为针孔,３为样品台,４为波带片.全场纳米显微系统全长约１m,椭球镜安装在距光源３３m 处.安装
在聚焦镜前方的光束挡光器和后方的针孔用来遮挡直通光和杂散光,样品放在三维可调节、可旋转的高精度
１０３４００２Ｇ５
光 学 学 报
图７ 外环发散角的拟合曲线
Fig敭７ Fittedcurveofdivergenceangleofoutsidering
图８ TXM 成像实验装置图
Fig敭８ Pictureofexperimentalsetup
的样品台上.探测器放置在距波带片约６０cm 处.
在椭球镜前端约３cm 处放置了直径为２００μm 的光束挡光器,用来遮挡直通光,从而提高系统的信噪
比.同时在椭球镜的后端大约１２cm 处放置直径为７０μm 的针孔,其作用是用来遮挡杂散光.样品放在四
维可调的高精度旋转样品台上;菲涅耳波带片购于瑞士保罗􀅰谢勒研究所[２０Ｇ２２],其具体参数如表２所示.波
带片放置在样品台后方三维可调的台面上.
图９ TXM 成像结果.(a)整体成像图;(b)在５００nm 分辨率附近的靶射线强度分布
Fig敭９ ImagingresultsofTXM敭 a Overallimagingpicture b intensityprofileoftargetradialnearresolutionratioof５００nm
表２ 波带片参数
Table２ Parametersofzoneplate
Fresnelzone
plate
Diameter/μm
Outermostzone
width/nm
Zone
material
Structure
height/nm
Focal
length/mm
Objectivelens
Electroplatedgold
５６．
探测器为１０×透镜耦合,单像素尺寸为６．
５μm×６．
５μm,探测器放置于距波带片后方６００mm 处,整个
系统的放大倍数为１１０倍,每个像素尺寸为５９nm×５９nm.能量为９keV,最小结构为５００nm 星型靶,曝
光时间为２００s.图９为TXM 成像图.在视场中可以清晰地分辨出相邻的两条靶射线,说明基于自行研制
的椭球镜实现了X 射线纳米成像.
１０３４００２Ｇ６
光 学 学 报

## sec:section-2 ４ 结 论
_Pages 7-8_

针对TXM 成像用最外环带宽为７０nm 的波带片,设计并成功拉制了与之匹配的单毛细管椭球镜.光
学检测结果表明,该椭球镜具有较高的质量,面形误差达到了１５μrad;X 射线检测到聚焦光斑尺寸为
４０μm,最大发射角为１．
７５mrad,工作距离为１６０．
９mm,满足了设计指标的要求.基于该椭球镜在上海光
源成像线站成功搭建了TXM 成像系统,并实现了纳米成像,表明研制的椭球镜可满足纳米成像的需求.
虽然基于自行研制的椭球聚焦镜初步实现了TXM 成像,但是从X 射线远场检测的结果可以发现,聚焦
圆环的均匀性并不太理想,聚焦光斑较大,这是因为研制的椭球镜的面形误差较大.在接下来的工作中,将
继续改进椭球镜的拉制工艺与检测方法,以减小椭球镜的面形误差,希望基于研制的椭球镜可以实现２０nm
分辨率的TXM 成像.
参
考
文
献
１ CroninJS ChenＧWiegartY K WangJ etal敭ThreeＧdimensionalreconstructionandanalysisofanentiresolidoxide
fuelcellbyfullＧfieldtransmissionXＧraymicroscopy J 敭JournalofPowerSources ２０１３ ２３３ １７４Ｇ１７９敭
２ LiuY AndrewsJ C Wang J etal敭Phaseretrievalusing polychromaticilluminationfortransmission XＧray
microscopy J 敭OpticsExpress ２０１１ １９ ２ ５４０Ｇ５４５敭
３ LiWenjie敭Studyontheapplicationof３DimgaeprocessingandanalysisfornanoＧCT D 敭Hefei UniversityofScience
andTechnoloyofChina ２０１１ ２０Ｇ２１敭
李文杰敭纳米CT 三维图像处理分析方法及其应用的研究 D 敭合肥 中国科学技术大学 ２０１１ ２０Ｇ２１敭
４ WangS WangD WuQ etal敭３DimagingofaricepollengrainusingtransmissionXＧraymicroscopy J 敭Journalof
SynchrotronRadiation ２０１５ ２２ ４ １０９１Ｇ１０９５敭
５ ChenT Y ChenYT WangCL etal敭FullＧfieldmicroimagingwith８keVXＧraysachievesaspatialresolutionsbetter
than２０nm J 敭OpticsExpress ２０１１ １９ ２１ １９９１９Ｇ１９９２４敭
６ ChenＧWiegartY K LiuZ FaberK T etal敭３DanalysisofaLiCoO２ＧLi Ni
１ ３Mn１ ３Co１ ３ O２LiＧionbatterypositive
electrodeusingXＧraynanoＧtomography J 敭ElectrochemistryCommunications ２０１３ ２８ １２７Ｇ１３０敭
７ BilderbackD H ThielDJ PahlR etal敭XＧrayapplicationswithglassＧcapillaryoptics J 敭JournalofSynchrotron
Radiation １９９４ １ １ ３７Ｇ４２敭
８ KumakhovM A敭Channelingofphotonsandnew XＧrayoptics J 敭NuclearInstrumentsand Methodsin Physics
ResearchSectionB １９９０ ４８ １ ２８３Ｇ２８６敭
９ XiaoQF PoturaevSV敭PolycapillaryＧbasedXＧrayoptics J 敭NuclearInstrumentsand MethodsinPhysicsResearch
SectionA １９９４ ３４７ １ ２ ３ ３７６Ｇ３８３敭
１０ LimJ Kim H ParkS Y敭Hard XＧraynanotomographybeamline７C XNIatPLSＧII J 敭JournalofSynchrotron
Radiation ２０１４ ２１ ４ ８２７Ｇ８３１敭
１１ JefimovsK VilaＧComamalaJ StampanoniM etal敭BeamＧshapingcondenserlensesforfullＧfieldtransmissionXＧray
microscopy J 敭JournalofSynchrotronRadiation ２００８ １５ １ １０６Ｇ１０８敭
１２ HuangR BilderbackD H敭SingleＧbouncemonocapillariesforfocusingsynchrotronradiation modeling measurements
andtheoreticallimits J 敭JournalofSynchrotronRadiation ２００６ １３ １ ７４Ｇ８４敭
１３ LinXY LiYD SunTX etal敭SimulationofXＧraytransmissionthroughanellipsoidalcapillary J 敭ChinesePhysics
B ２０１０ １９ ７ ０７０２０５敭
１４ JinTianping LiWenjie ChenJie etal敭ThedesignandtestofellipsoidalglasscapillariesascondensersforXＧray
microscope J 敭NuclearTechniques ２００８ ３１ ９ ６７１Ｇ６７５敭
金田萍 李文杰 陈洁 等敭X 射线成像椭球聚焦镜的设计与检测 J 敭核技术 ２００８ ３１ ９ ６７１Ｇ６７５敭
１５ ZengX DuewerF FeserM etal敭EllipsoidalandparabolicglasscapillariesascondensersforXＧraymicroscopes J 敭
AppliedOptics ２００８ ４７ １３ ２３７６Ｇ２３８１敭
１６ FengB DengB RenY etal敭FullＧfieldXＧraynanoＧimagingsystemdesignedandconstructedatSSRF J 敭Chinese
OpticsLetters ２０１６ １４ ９ ０９３４０１敭
１７ WangFeixiang DengBiao WangYudan etal敭ThesynchrotronradiationXＧraystereoimagingbasedoncapillary
beamsplit J 敭ActaOpticaSinica ２０１６ ３６ ８ ０８３４００４敭
王飞翔 邓彪 王玉丹 等敭基于毛细管分光的同步辐射X 射线立体成像 J 敭光学学报 ２０１６ ３６ ８ ０８３４００４敭
１８ XiaoTiqiao XieHonglan DengBiao etal敭ProgressofXＧrayimagingmethodologyanditsapplicationsatShanghai
１０３４００２Ｇ７
光 学 学 报
synchrotronradiationfacility J 敭ActaOpticaSinica ２０１４ ３４ １ ０１００００１敭
肖体乔 谢红兰 邓彪 等敭上海光源X 射线成像及其应用研究进展 J 敭光学学报 ２０１４ ３４ １ ０１００００１敭
１９ TengYuepeng SunTianxi LiuZhiguo etal敭NewtypemonocapillaryXＧrayopticaldevice J 敭ActaOpticaSinica
２０１０ ３０ ２ ５４２Ｇ５４５敭
滕玥鹏 孙天希 刘志国 等敭一种新型单毛细管X 光学器件 J 敭光学学报 ２０１０ ３０ ２ ５４２Ｇ５４５敭
２０ GorelickS VilaＧComamalaJ GuzenkoV A etal敭HighＧefficiencyFresnelzoneplatesforhardXＧraysby１００keV
eＧbeamlithographyandelectroplating J 敭JournalofSynchrotronRadiation ２０１１ １８ ３ ４４２Ｇ４４６敭
２１ MoksoR QuaroniL MaroneF etal敭XＧray mosaicnanotomographyoflarge microorganisms J 敭Journalof
StructuralBiology ２０１２ １７７ ２ ２３３Ｇ２３８敭
２２ StampanoniM Mokso R MaroneF etal敭PhaseＧcontrasttomographyatthenanoscaleusinghard XＧrays J 敭
PhysicalReviewB ２０１０ ８１ １４ １４０１０５敭
１０３４００２Ｇ８
