<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>马戛尔尼访华礼单对比 - 清朝盛世背后的危机</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <style>
        /* 新增：让HTML根节点背景透明（核心） */
        html {
            background: transparent !important;
        }
        /* 礼物散落动画 */
        @keyframes giftFall {
            0% { opacity: 0; transform: translateY(-50px) rotate(0deg); }
            100% { opacity: 1; transform: translateY(0) rotate(var(--rotate, 0deg)); }
        }
        .gift-item {
            animation: giftFall 0.8s ease forwards;
            animation-delay: calc(var(--index) * 0.1s);
            pointer-events: auto;
            display: flex;
            align-items: center;
            justify-content: center;
            padding: 0 !important;
            background: transparent !important;
            border: none !important;
            cursor: pointer; /* 添加点击光标样式 */
        }
        /* 礼物图片样式：占满整个容器，无多余样式 */
        .gift-img {
            width: 100%;
            height: 100%;
            object-fit: contain; /* 保持图片比例，不拉伸 */
            border-radius: 6px;
            transition: transform 0.2s ease; /* 点击前的微动效 */
        }
        .gift-item:hover .gift-img {
            transform: scale(1.05); /* 悬浮放大效果 */
        }
        /* 隐藏礼物名称 */
        .gift-name {
            display: none !important;
        }
        /* 悬浮提示框 */
        .gift-tooltip {
            display: none;
            position: absolute;
            z-index: 99;
            width: 280px;
            padding: 12px;
            background: rgba(0, 0, 0, 0.85);
            color: #fff;
            border-radius: 8px;
            font-size: 14px;
            line-height: 1.5;
            box-shadow: 0 4px 12px rgba(0,0,0,0.3);
        }
        /* 礼箱容器：核心适配图片显示（移除白色背景相关样式） */
        .box-wrap {
            position: relative;
            width: 100%;
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 300px;
            background: transparent !important; /* 强制透明 */
        }
        /* 礼箱图片：防拉伸+自适应+鼠标样式 */
        .box-img {
            max-width: 100%;
            max-height: 300px;
            object-fit: contain;
            cursor: pointer;
            transition: transform 0.3s ease-in-out;
        }
        .box-img:hover {
            transform: scale(1.03);
        }
        /* 礼物容器：绝对定位在礼箱上方，不遮挡点击 */
        .gifts-wrap {
            position: absolute;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            width: 90%;
            height: 90%;
            z-index: 10;
            flex-wrap: wrap;
            gap: 8px !important; /* 调整图片间距更自然 */
            background: transparent !important; /* 强制透明 */
        }
        /* 礼物弹窗样式 */
        .gift-modal-overlay {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100vw;
            height: 100vh;
            background: rgba(0, 0, 0, 0.9);
            z-index: 100; /* 高于提示框 */
            justify-content: center;
            align-items: center;
            padding: 20px;
            backdrop-filter: blur(4px); /* 背景模糊效果 */
        }
        .gift-modal {
            background: #fff;
            border-radius: 12px;
            max-width: 90%;
            max-height: 90vh;
            display: flex;
            flex-direction: column;
            overflow: auto;
            box-shadow: 0 8px 32px rgba(0,0,0,0.5);
            animation: modalShow 0.3s ease forwards;
        }
        /* 弹窗显示动画 */
        @keyframes modalShow {
            0% { opacity: 0; transform: scale(0.9); }
            100% { opacity: 1; transform: scale(1); }
        }
        .gift-modal-img {
            width: 100%;
            max-width: 600px;
            max-height: 450px;
            object-fit: contain;
            border-radius: 8px 8px 0 0;
        }
        .gift-modal-info {
            padding: 20px 24px;
            color: #333;
            line-height: 1.8;
            font-size: 16px;
        }
        /* 响应式调整弹窗 */
        @media (max-width: 768px) {
            .gift-modal-img {
                max-height: 300px;
            }
            .gift-modal-info {
                font-size: 14px;
                padding: 16px 20px;
            }
        }
    </style>
</head>
<!-- 关键改动：body的bg-gray-100（浅灰色）改为bg-transparent（透明），移除多余背景色 -->
<body class="bg-transparent min-h-screen p-4 md:p-8">
    <!-- 核心容器强制透明 -->
    <div class="max-w-7xl mx-auto bg-transparent">
        <!-- 核心对比容器 -->
        <div class="flex flex-col md:flex-row justify-between gap-6 md:gap-8 bg-transparent">
            <!-- 左侧：英国使团赠乾隆 -->
            <div class="w-full md:w-1/2 p-4 md:p-6 bg-transparent">
                <div class="box-wrap">
                    <!-- 英国礼箱 -->
                    <img id="ukBox" class="box-img" 
                         data-status="closed"
                         src="https://p3-flow-imagex-sign.byteimg.com/tos-cn-i-a9rns2rl98/ee49e7905cad4129a08aa6fd765fd61f.png~tplv-a9rns2rl98-image.png?lk3s=8e244e95&rcl=20260130160422E6ADA813585F2F2821A8&rrcfp=dafada99&x-expires=2085984262&x-signature=uLtgrmhy2M7YY%2B%2Bz1cHQHyaGaJ4%3D" 
                         alt="英国关闭的礼箱">
                    <!-- 英国礼物列表 -->
                    <div id="ukGifts" class="gifts-wrap hidden flex flex-wrap items-center justify-center gap-3 md:gap-4">
                        <!-- 1. 两截凤枪 -->
                        <div class="gift-item w-20 h-20 md:w-24 md:h-24 rounded-lg" 
                             style="--rotate: -5deg; --index: 1"
                             data-name="两截凤枪"
                             data-tech="气火两用，模块化设计。枪管分为两截，可组合使用。既能作为传统燧发枪，也可接驳充气球作为气压枪，无需火药。体现了多功能、可转换的模块化设计思想。"
                             data-history="超越了单一功能思维，展现了英国武器设计中的创新性与实用性追求。对清廷而言，这或许只是“奇巧”之物，其背后的科学原理（气体力学）与设计哲学未被探究。">
                            <img src="https://p3-flow-imagex-download-sign.byteimg.com/tos-cn-i-a9rns2rl98/49160deaf34447649b5894bc23d3f736.png~tplv-a9rns2rl98-24:720:720.png?lk3s=8e244e95&rcl=2026013016170591518070D1A4C6300816&rrcfp=8a172a1a&x-expires=1770365825&x-signature=ekNBjmeZ1kqS9MKZYkO5ZLkoMpM%3D" 
                                 class="gift-img" alt="两截凤枪" 
                                 onerror="this.src='data:image/svg+xml;utf8,<svg xmlns=&quot;http://www.w3.org/2000/svg&quot; width=&quot;100&quot; height=&quot;100&quot;><text x=&quot;50%&quot; y=&quot;50%&quot; text-anchor=&quot;middle&quot; fill=&quot;#666&quot;>两截凤枪</text></svg>'">
                        </div>
                        <!-- 2. 榴弹炮车 -->
                        <div class="gift-item w-20 h-20 md:w-24 md:h-24 rounded-lg" 
                             style="--rotate: 8deg; --index: 2"
                             data-name="榴弹炮车"
                             data-tech="铸钢炮管+实木炮架，车轮采用辐条式设计，炮身刻有弹道刻度，可快速调整射击角度，射程超1500米"
                             data-history="英国陆军制式装备，体现近代火炮制造的标准化与实用性，代表最前沿的军事科技。乾隆认为其巨大的杀伤力有违“仁慈治天下”的观念，其被原封不动地送入圆明园库房。">
                            <img src="https://p3-flow-imagex-download-sign.byteimg.com/tos-cn-i-a9rns2rl98/cdb31e7a1aba46c1a2fcf85e00370829.png~tplv-a9rns2rl98-24:720:720.png?lk3s=8e244e95&rcl=2026013016170591518070D1A4C6300816&rrcfp=8a172a1a&x-expires=1770365825&x-signature=08%2Bnzy1elfNNEKY5IhxXHllfL7Y%3D" 
                                 class="gift-img" alt="榴弹炮车"
                                 onerror="this.src='data:image/svg+xml;utf8,<svg xmlns=&quot;http://www.w3.org/2000/svg&quot; width=&quot;100&quot; height=&quot;100&quot;><text x=&quot;50%&quot; y=&quot;50%&quot; text-anchor=&quot;middle&quot; fill=&quot;#666&quot;>榴弹炮车</text></svg>'">
                        </div>
                        <!-- 3. 四轮马车 -->
                        <div class="gift-item w-20 h-20 md:w-24 md:h-24 rounded-lg" 
                             style="--rotate: -3deg; --index: 3"
                             data-name="四轮马车"
                             data-tech="实木车架+弹簧减震装置，车轮橡胶包边，车厢采用皮革内饰，转向系统可灵活调整。内设减震弹簧，相较中国两轮马车稳定性更强，速度快，车厢装有透明的玻璃窗和百叶窗。"
                             data-history="英国近代交通工业的代表，体现机械设计与民用制造的结合，是工业革命生活方式升级的标志">
                            <img src="https://p3-flow-imagex-download-sign.byteimg.com/tos-cn-i-a9rns2rl98/8cfc100f649d4a28bce276052be34b37.png~tplv-a9rns2rl98-24:720:720.png?lk3s=8e244e95&rcl=2026013016170591518070D1A4C6300816&rrcfp=8a172a1a&x-expires=1770365825&x-signature=61bh3Zwl2%2BbwKsh7aTmdSTrKvJ0%3D" 
                                 class="gift-img" alt="四轮马车"
                                 onerror="this.src='data:image/svg+xml;utf8,<svg xmlns=&quot;http://www.w3.org/2000/svg&quot; width=&quot;100&quot; height=&quot;100&quot;><text x=&quot;50%&quot; y=&quot;50%&quot; text-anchor=&quot;middle&quot; fill=&quot;#666&quot;>四轮马车</text></svg>'">
                        </div>
                        <!-- 4. 铜板图画 -->
                        <div class="gift-item w-20 h-20 md:w-24 md:h-24 rounded-lg" 
                             style="--rotate: 10deg; --index: 4"
                             data-name="铜板图画"
                             data-tech="共16册，2108页，采用高品质铜版印刷，真实细致地展现了英国的城市、建筑、舰队、战争场景与王室生活，宛如一部图像百科全书。"
                             data-history="英国有意识的国家形象展示，旨在传递其国力与文明程度。清廷将其定为“铜版图画”收储，更多是欣赏其印刷技艺与“异域风情”，可能忽略了图像背后所承载的社会制度、军事组织与海外扩张信息。">
                            <img src="https://p26-flow-imagex-download-sign.byteimg.com/tos-cn-i-a9rns2rl98/bfeb45721b77424ba8efaec878354472.png~tplv-a9rns2rl98-24:720:720.png?lk3s=8e244e95&rcl=2026013016170591518070D1A4C6300816&rrcfp=8a172a1a&x-expires=1770365825&x-signature=LgaUM3vonKGPRj2fW5SDx5OuzkQ%3D" 
                                 class="gift-img" alt="铜板图画"
                                 onerror="this.src='data:image/svg+xml;utf8,<svg xmlns=&quot;http://www.w3.org/2000/svg&quot; width=&quot;100&quot; height=&quot;100&quot;><text x=&quot;50%&quot; y=&quot;50%&quot; text-anchor=&quot;middle&quot; fill=&quot;#666&quot;>铜板图画</text></svg>'">
                        </div>
                        <!-- 5. 望远镜、反射式望远镜、量角仪 -->
                        <div class="gift-item w-20 h-20 md:w-24 md:h-24 rounded-lg" 
                             style="--rotate: -8deg; --index: 5"
                             data-name="望远镜套件"
                             data-tech="有赫舍尔望远镜、折射式望远镜和量角仪，黄铜镀金工艺防锈。配合天体运行仪，可以清楚地观测到天体各部分是如何运行的，和天体上标示的完全一致。赫舍尔望远镜通过主镜反射来观测目标，望远范围大大增加。"
                             data-history="英国近代天文观测技术的代表，体现对自然科学的精准探索，是航海、军事观测的核心工具">
                            <img src="https://p26-flow-imagex-download-sign.byteimg.com/tos-cn-i-a9rns2rl98/a06fafac36134414a9844a10749752f9.png~tplv-a9rns2rl98-24:720:720.png?lk3s=8e244e95&rcl=2026013016170591518070D1A4C6300816&rrcfp=8a172a1a&x-expires=1770365825&x-signature=1SDn7XmKnIPrCuJy5uxSaiq%2Fzis%3D" 
                                 class="gift-img" alt="望远镜套件"
                                 onerror="this.src='data:image/svg+xml;utf8,<svg xmlns=&quot;http://www.w3.org/2000/svg&quot; width=&quot;100&quot; height=&quot;100&quot;><text x=&quot;50%&quot; y=&quot;50%&quot; text-anchor=&quot;middle&quot; fill=&quot;#666&quot;>望远镜套件</text></svg>'">
                        </div>
                        <!-- 6. 音乐钟 -->
                        <div class="gift-item w-20 h-20 md:w-24 md:h-24 rounded-lg" 
                             style="--rotate: 5deg; --index: 6"
                             data-name="音乐钟"
                             data-tech="机械摆轮机芯+黄铜镀金外壳，内置12首西洋乐曲，钟摆误差每日≤1分钟，雕刻纹饰采用镂空技法"
                             data-history="英国钟表制造业的巅峰之作，融合机械传动与声学设计，体现精密机械加工能力与艺术审美结合">
                            <img src="https://p3-flow-imagex-download-sign.byteimg.com/tos-cn-i-a9rns2rl98/2eb5b2d352de4fc6bb32eb85ab18b575.png~tplv-a9rns2rl98-24:720:720.png?lk3s=8e244e95&rcl=2026013016170591518070D1A4C6300816&rrcfp=8a172a1a&x-expires=1770365825&x-signature=2DCXT0WDN1c1Yk44Qqjn9lnsW38%3D" 
                                 class="gift-img" alt="音乐钟"
                                 onerror="this.src='data:image/svg+xml;utf8,<svg xmlns=&quot;http://www.w3.org/2000/svg&quot; width=&quot;100&quot; height=&quot;100&quot;><text x=&quot;50%&quot; y=&quot;50%&quot; text-anchor=&quot;middle&quot; fill=&quot;#666&quot;>音乐钟</text></svg>'">
                        </div>
                        <!-- 7. 自来火枪 -->
                        <div class="gift-item w-20 h-20 md:w-24 md:h-24 rounded-lg" 
                             style="--rotate: -7deg; --index: 7"
                             data-name="自来火枪"
                             data-tech="采用旋转燧石摩擦发火的先进构造，击发可靠。枪管由伦敦兵工厂精密铸造镗孔，内壁光滑。枪身胡桃木制，关键部位以黄铜加固并镶嵌金银，兼具强度与防腐蚀。"
                             data-history="体现了标准化、精密化的近代军工理念。英国近代轻武器技术的标杆，标准化生产工艺远超同时期清朝火绳枪，体现军工工业化优势。">
                            <img src="https://p11-flow-imagex-download-sign.byteimg.com/tos-cn-i-a9rns2rl98/4478502c46cc4439bb9d55356e25dc69.png~tplv-a9rns2rl98-24:720:720.png?lk3s=8e244e95&rcl=2026013016170591518070D1A4C6300816&rrcfp=8a172a1a&x-expires=1770365825&x-signature=uV%2F5fIEm7xBNFzaAgMpAtf16b1Y%3D" 
                                 class="gift-img" alt="自来火枪"
                                 onerror="this.src='data:image/svg+xml;utf8,<svg xmlns=&quot;http://www.w3.org/2000/svg&quot; width=&quot;100&quot; height=&quot;100&quot;><text x=&quot;50%&quot; y=&quot;50%&quot; text-anchor=&quot;middle&quot; fill=&quot;#666&quot;>自来火枪</text></svg>'">
                        </div>
                    </div>
                </div>
            </div>

            <!-- 右侧：乾隆回赠英国国王 -->
            <div class="w-full md:w-1/2 p-4 md:p-6 bg-transparent">
                <div class="box-wrap">
                    <!-- 清朝礼箱 -->
                    <img id="qingBox" class="box-img" 
                         data-status="closed"
                         src="https://p9-flow-imagex-sign.byteimg.com/tos-cn-i-a9rns2rl98/c601b752e270429a8aef167ae9b19041.png~tplv-a9rns2rl98-image.png?lk3s=8e244e95&rcl=20260130160422E6ADA813585F2F2821A8&rrcfp=dafada99&x-expires=2085984262&x-signature=cTjibEOWjEish62kOO0u6FNTkLc%3D" 
                         alt="清朝关闭的礼箱">
                    <!-- 清朝礼物列表 -->
                    <div id="qingGifts" class="gifts-wrap hidden flex flex-wrap items-center justify-center gap-3 md:gap-4">
                        <!-- 1. 青龙瓷大缸 -->
                        <div class="gift-item w-20 h-20 md:w-24 md:h-24 rounded-lg" 
                             style="--rotate: 6deg; --index: 1"
                             data-name="青龙瓷大缸"
                             data-tech="巨型官窑瓷器，采用高岭土为原料，分段拉坯、拼接成型，高温一次烧制，缸身绘青龙纹，釉色莹润"
                             data-history="清朝大型瓷器制造的代表，体现传统手工业的精湛技艺，无科技创新">
                            <img src="https://p3-flow-imagex-download-sign.byteimg.com/tos-cn-i-a9rns2rl98/cbc06462c3fc447abc7ea57e22c9adec.png~tplv-a9rns2rl98-24:720:720.png?lk3s=8e244e95&rcl=20260130180737E8444C7CD27BC82D614B&rrcfp=8a172a1a&x-expires=1770372457&x-signature=InUb%2By9wASrlo%2FzxkF0GoGvuNjQ%3D" 
                                 class="gift-img" alt="青龙瓷大缸"
                                 onerror="this.src='data:image/svg+xml;utf8,<svg xmlns=&quot;http://www.w3.org/2000/svg&quot; width=&quot;100&quot; height=&quot;100&quot;><text x=&quot;50%&quot; y=&quot;50%&quot; text-anchor=&quot;middle&quot; fill=&quot;#666&quot;>青龙瓷大缸</text></svg>'">
                        </div>
                        <!-- 2. 普洱茶膏 -->
                        <div class="gift-item w-20 h-20 md:w-24 md:h-24 rounded-lg" 
                             style="--rotate: -4deg; --index: 2"
                             data-name="普洱茶膏"
                             data-tech="采用云南普洱熟茶为原料，经熬制、过滤、浓缩、定型等工序制成，膏体细腻，便于储存和携带"
                             data-history="清朝宫廷御用茶制品，是传统制茶工艺的延伸，属手工业精加工范畴">
                            <img src="https://p11-flow-imagex-download-sign.byteimg.com/tos-cn-i-a9rns2rl98/b20fa622ff904b6c9dc78dee0d5e0e98.png~tplv-a9rns2rl98-24:720:720.png?lk3s=8e244e95&rcl=20260130180737E8444C7CD27BC82D614B&rrcfp=8a172a1a&x-expires=1770372457&x-signature=ok7FqRHJqygs87IOssPSgWmSKsg%3D" 
                                 class="gift-img" alt="普洱茶膏"
                                 onerror="this.src='data:image/svg+xml;utf8,<svg xmlns=&quot;http://www.w3.org/2000/svg&quot; width=&quot;100&quot; height=&quot;100&quot;><text x=&quot;50%&quot; y=&quot;50%&quot; text-anchor=&quot;middle&quot; fill=&quot;#666&quot;>普洱茶膏</text></svg>'">
                        </div>
                        <!-- 3. 青花瓷有盖壮罐 -->
                        <div class="gift-item w-20 h-20 md:w-24 md:h-24 rounded-lg" 
                             style="--rotate: 9deg; --index: 3"
                             data-name="青花瓷有盖壮罐"
                             data-tech="景德镇官窑烧制，采用浙料青花发色，多层纹饰构图，盖与罐身严丝合缝，胎体坚致，釉面莹润"
                             data-history="清朝青花瓷器的经典器型，体现传统制瓷工艺的成熟，无技术突破">
                            <img src="https://p3-flow-imagex-download-sign.byteimg.com/tos-cn-i-a9rns2rl98/61733bc4c9cc433f9a3edcc9a09661f0.png~tplv-a9rns2rl98-24:720:720.png?lk3s=8e244e95&rcl=20260130180737E8444C7CD27BC82D614B&rrcfp=8a172a1a&x-expires=1770372457&x-signature=Nejsl%2BmfN5QzmReQP6eJToz7vlY%3D" 
                                 class="gift-img" alt="青花瓷有盖壮罐"
                                 onerror="this.src='data:image/svg+xml;utf8,<svg xmlns=&quot;http://www.w3.org/2000/svg&quot; width=&quot;100&quot; height=&quot;100&quot;><text x=&quot;50%&quot; y=&quot;50%&quot; text-anchor=&quot;middle&quot; fill=&quot;#666&quot;>青花瓷有盖壮罐</text></svg>'">
                        </div>
                        <!-- 4. 红雕漆小顶柜 -->
                        <div class="gift-item w-20 h-20 md:w-24 md:h-24 rounded-lg" 
                             style="--rotate: -7deg; --index: 4"
                             data-name="红雕漆小顶柜"
                             data-tech="采用剔红技法，以红漆层层髹涂（达百层以上），经雕刻、打磨，纹饰为山水人物纹，雕工精细，造型典雅"
                             data-history="清朝雕漆工艺的代表，传统宫廷家具，属手工雕刻艺术范畴">
                            <img src="https://p11-flow-imagex-download-sign.byteimg.com/tos-cn-i-a9rns2rl98/ff14ee0cb1be4b519669a576be90bfe6.png~tplv-a9rns2rl98-24:720:720.png?lk3s=8e244e95&rcl=20260130180737E8444C7CD27BC82D614B&rrcfp=8a172a1a&x-expires=1770372457&x-signature=3lv5Uvg8vl1wCRb%2FRzBibgUR6xs%3D" 
                                 class="gift-img" alt="红雕漆小顶柜"
                                 onerror="this.src='data:image/svg+xml;utf8,<svg xmlns=&quot;http://www.w3.org/2000/svg&quot; width=&quot;100&quot; height=&quot;100&quot;><text x=&quot;50%&quot; y=&quot;50%&quot; text-anchor=&quot;middle&quot; fill=&quot;#666&quot;>红雕漆小顶柜</text></svg>'">
                        </div>
                        <!-- 5. 碧玉如意 -->
                        <div class="gift-item w-20 h-20 md:w-24 md:h-24 rounded-lg" 
                             style="--rotate: 3deg; --index: 5"
                             data-name="碧玉如意"
                             data-tech="选用新疆和田碧玉，经选料、雕刻、打磨、抛光多道工序，采用透雕、浮雕技法，纹饰为祥云纹，手感温润"
                             data-history="清朝宫廷御用礼器，是朝贡体系中“赏赐”的典型代表，象征皇权与吉祥">
                            <img src="https://p11-flow-imagex-download-sign.byteimg.com/tos-cn-i-a9rns2rl98/bef8111f32ad4185a11d1e6fdfb0a199.png~tplv-a9rns2rl98-24:720:720.png?lk3s=8e244e95&rcl=20260130180737E8444C7CD27BC82D614B&rrcfp=8a172a1a&x-expires=1770372457&x-signature=SHvNCyTwema5QJIiw70vpY%2FqV6o%3D" 
                                 class="gift-img" alt="碧玉如意"
                                 onerror="this.src='data:image/svg+xml;utf8,<svg xmlns=&quot;http://www.w3.org/2000/svg&quot; width=&quot;100&quot; height=&quot;100&quot;><text x=&quot;50%&quot; y=&quot;50%&quot; text-anchor=&quot;middle&quot; fill=&quot;#666&quot;>碧玉如意</text></svg>'">
                        </div>
                    </div>
                </div>
            </div>
        </div>

        <!-- 悬浮提示框（全局共用） -->
        <div class="gift-tooltip" id="giftTooltip"></div>
        
        <!-- 礼物弹窗 -->
        <div class="gift-modal-overlay" id="giftModalOverlay">
            <div class="gift-modal" id="giftModal">
                <img class="gift-modal-img" id="giftModalImg" alt="礼物详情">
                <div class="gift-modal-info" id="giftModalInfo"></div>
            </div>
        </div>
    </div>

    <script>
        // 1. 基础元素获取
        const ukBoxImg = document.getElementById('ukBox');
        const ukGifts = document.getElementById('ukGifts');
        const qingBoxImg = document.getElementById('qingBox');
        const qingGifts = document.getElementById('qingGifts');
        const tooltip = document.getElementById('giftTooltip');
        // 弹窗相关元素
        const modalOverlay = document.getElementById('giftModalOverlay');
        const modal = document.getElementById('giftModal');
        const modalImg = document.getElementById('giftModalImg');
        const modalInfo = document.getElementById('giftModalInfo');

        // 2. 礼箱图片URL常量
        const UK_BOX_CLOSED = "https://p3-flow-imagex-sign.byteimg.com/tos-cn-i-a9rns2rl98/ee49e7905cad4129a08aa6fd765fd61f.png~tplv-a9rns2rl98-image.png?lk3s=8e244e95&rcl=20260130160422E6ADA813585F2F2821A8&rrcfp=dafada99&x-expires=2085984262&x-signature=uLtgrmhy2M7YY%2B%2Bz1cHQHyaGaJ4%3D";
        const UK_BOX_OPEN = "https://p3-flow-imagex-sign.byteimg.com/tos-cn-i-a9rns2rl98/ac2241e59a1940ae9d40a01ded3d53f1.png~tplv-a9rns2rl98-image.png?lk3s=8e244e95&rcl=20260130160422E6ADA813585F2F2821A8&rrcfp=dafada99&x-expires=2085984262&x-signature=PkqJL%2FKg%2BQHwcukumvpdmE0CQvI%3D";
        const QING_BOX_CLOSED = "https://p9-flow-imagex-sign.byteimg.com/tos-cn-i-a9rns2rl98/c601b752e270429a8aef167ae9b19041.png~tplv-a9rns2rl98-image.png?lk3s=8e244e95&rcl=20260130160422E6ADA813585F2F2821A8&rrcfp=dafada99&x-expires=2085984262&x-signature=cTjibEOWjEish62kOO0u6FNTkLc%3D";
        const QING_BOX_OPEN = "https://p3-flow-imagex-sign.byteimg.com/tos-cn-i-a9rns2rl98/5bc3f7f0e778437e87d2ad77d3b62b90.png~tplv-a9rns2rl98-image.png?lk3s=8e244e95&rcl=20260130160422E6ADA813585F2F2821A8&rrcfp=dafada99&x-expires=2085984262&x-signature=EhuBcda8xkIUUxwXIGV54tv1HNM%3D";

        // 3. 英国礼箱切换逻辑
        ukBoxImg.addEventListener('click', () => {
            const status = ukBoxImg.getAttribute('data-status');
            if (status === 'closed') {
                ukBoxImg.src = UK_BOX_OPEN;
                ukBoxImg.setAttribute('data-status', 'open');
                ukGifts.classList.remove('hidden');
            } else {
                ukBoxImg.src = UK_BOX_CLOSED;
                ukBoxImg.setAttribute('data-status', 'closed');
                ukGifts.classList.add('hidden');
            }
        });

        // 4. 清朝礼箱切换逻辑
        qingBoxImg.addEventListener('click', () => {
            const status = qingBoxImg.getAttribute('data-status');
            if (status === 'closed') {
                qingBoxImg.src = QING_BOX_OPEN;
                qingBoxImg.setAttribute('data-status', 'open');
                qingGifts.classList.remove('hidden');
            } else {
                qingBoxImg.src = QING_BOX_CLOSED;
                qingBoxImg.setAttribute('data-status', 'closed');
                qingGifts.classList.add('hidden');
            }
        });

        // 5. 礼物悬浮提示功能
        const allGifts = document.querySelectorAll('.gift-item');
        allGifts.forEach(gift => {
            // 悬浮显示提示（名称+核心工艺）
            gift.addEventListener('mouseover', (e) => {
                const name = gift.getAttribute('data-name');
                const tech = gift.getAttribute('data-tech');
                // 拼接提示内容，保持格式美观
                tooltip.innerHTML = `<strong>【${name}】</strong><br><br>核心工艺：${tech}`;
                tooltip.style.display = 'block';
                updateTooltipPos(e);
            });
            // 鼠标移动跟随
            gift.addEventListener('mousemove', updateTooltipPos);
            // 离开隐藏
            gift.addEventListener('mouseout', () => {
                tooltip.style.display = 'none';
            });

            // 6. 礼物点击弹窗功能（仅显示历史解读）
            gift.addEventListener('click', (e) => {
                e.stopPropagation(); // 阻止冒泡到遮罩层
                // 获取礼物图片和历史解读
                const giftImg = gift.querySelector('.gift-img');
                const imgSrc = giftImg.src;
                const name = gift.getAttribute('data-name');
                const history = gift.getAttribute('data-history');
                // 填充弹窗内容
                modalImg.src = imgSrc;
                modalImg.alt = giftImg.alt;
                modalInfo.innerHTML = `<h3 class="text-xl font-bold mb-3">【${name} - 历史解读】</h3>${history}`;
                // 显示弹窗
                modalOverlay.style.display = 'flex';
                // 隐藏悬浮提示
                tooltip.style.display = 'none';
            });
        });

        // 7. 调整提示框位置
        function updateTooltipPos(e) {
            const tipW = tooltip.offsetWidth;
            const tipH = tooltip.offsetHeight;
            const winW = window.innerWidth;
            const winH = window.innerHeight;

            let left = e.pageX + 15;
            let top = e.pageY + 15;

            if (left + tipW > winW) left = e.pageX - tipW - 15;
            if (top + tipH > winH) top = e.pageY - tipH - 15;

            tooltip.style.left = `${left}px`;
            tooltip.style.top = `${top}px`;
        }

        // 8. 弹窗关闭逻辑
        // 点击遮罩层关闭
        modalOverlay.addEventListener('click', () => {
            modalOverlay.style.display = 'none';
        });
        // 点击弹窗内部不关闭
        modal.addEventListener('click', (e) => {
            e.stopPropagation();
        });
        // ESC键关闭
        document.addEventListener('keydown', (e) => {
            if (e.key === 'Escape' && modalOverlay.style.display === 'flex') {
                modalOverlay.style.display = 'none';
            }
        });

        // 9. 窗口缩放时隐藏提示框
        window.addEventListener('resize', () => {
            tooltip.style.display = 'none';
        });
    </script>
</body>
</html># zhongxilixiang
