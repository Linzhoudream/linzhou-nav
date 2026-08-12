
箱包 AI 视觉生成技能 · 全网同类调研与文件整合建议
调研日期：2026-08-12 ｜ 触发：用户提供 @电商图片生成技能.docx（baigou-bag-ai-vision）并询问”GitHub 有没有类似的、文件要不要补、对定时任务有没有参考价值” 配套动作：已依据 docx 在本仓库落地正式技能目录 skills/baigou-bag-ai-vision/
一、结论先行（TL;DR）
问题
结论
GitHub / 全网有没有类似技能？
有，且不止一个。 最贴近的是 buluslan/gpt-image2-ecommerce（25 模板 / MIT / codex CLI）、w-cyh 与 liangdabiao/ecom-details-image（25 模板 / Campaign Style Lock / GPT-Image-2 双模式）。此外 ConardLi/garden-skills、EvoLinkAI/awesome-gpt-image-2-prompts、Design Image Studio、skill-prompt-generator 都是同类不同形态。
我们的文件要不要补充 / 修改？
要补充，不必推倒重来。 我们 /workspace/skills/ 里已有一个成型电商出图技能 designkit-ecommerce-product-kit（对话式 + 美图 API，覆盖服饰配件/箱包邻接品类）。docx 的 baigou-bag-ai-vision 是箱包专属技能，补的是”箱包材质语言 + 防变形 + 四平台合规 + 离线便携”这一层。已新建独立技能目录，与既有 designkit 互补，不冲突。
对定时任务有没有参考价值？
有，但是”提示词生产模块”，不是”自动出图模块”。 每日主线 5017165 的 T5 是”只出 prompt 绝不自动出图”。本技能可让 T5 产出箱包专属、合规、带防变形约束的高质量提示词；但不应在定时任务里直接调 designkit/即梦 API 自动出图（耗 credits、需人工选风格、违背既定规则）。合规清单对每日内容质量也有校验价值。
二、Q1：GitHub / 全网同类技能盘点
2.1 直接对标（电商图片生成 Skill，结构高度相似）
仓库
核心能力
出图模式
模型 / API
模板数
箱包/皮具专属
合规/反AI感
许可
HYPERLINK "https://github.com/buluslan/gpt-image2-ecommerce"buluslan/gpt-image2-ecommerce
25 场景模板 + 智能匹配 + 参考图一致性
codex CLI 调 imagegen（可带参考图）
GPT-Image-2
25
❌ 通用，但支持参考图套用
✅ 内置 CCD 复古/可见瑕疵”反 AI 感”
MIT
HYPERLINK "https://github.com/w-cyh/ecom-details-image"w-cyh/ecom-details-image
25 模板 + Campaign Style Lock（多图锁色板/冷暖/字体一致）+ 转化驱动力诊断
Prompt / Generate 双模式（不配 API 只出 prompt，配了直接出图）
GPT-Image-2 / OpenAI 兼容
25
❌ 通用
—
—
HYPERLINK "https://github.com/liangdabiao/ecom-details-image"liangdabiao/ecom-details-image
同上（同一项目不同 fork）
双模式
GPT-Image-2
25
❌ 通用
—
—
关键共性：25 个场景模板 + 自然语言自动匹配模板 + 参考图保一致性 + Prompt/出图双模。这和 docx 里 baigou-bag-ai-vision 的”6+1 提示词体系 + 固定 5 张分镜 + 参考图/实拍图输入”思路一致，但 docx 更”垂直”——专门吃透箱包材质与平台合规。
2.2 周边同类（提示词库 / 设计推理型）
项目
形态
与本次关系
HYPERLINK "https://github.com/ConardLi/garden-skills"ConardLi/garden-skills（gpt-image-2）
18 大类 / 80+ 结构化模板 Skill，适配 Claude Code/Cursor/Codex/Gemini CLI
更”通才”，可借鉴其跨宿主兼容写法
HYPERLINK "https://github.com/EvoLinkAI/awesome-gpt-image-2-prompts"EvoLinkAI/awesome-gpt-image-2-prompts
GPT-Image-2 提示词合集
提示词素材来源，可抽取箱包相关句段
Design Image Studio（CSDN 报道）
保留完整”设计系统提示词”做设计推理 → 精准出图
思路差异：它重”设计简报推理”，docx 重”防变形+合规”
skill-prompt-generator（什么值得买）
12 领域专家，把口语转专业提示词
可参考其”口语→专业提示词”的降门槛思路
2.3 一个重要发现：我们自家已经有电商出图技能
/workspace/skills/designkit-skills/skills/designkit-ecommerce-product-kit/SKILL.md —— 一个已落地、可直连美图设计室 API的电商套图技能：
对话式分步收集（卖点 → 上架配置 → 爆款风格 → 成图自动下载 7 图）
覆盖 亚马逊/淘宝/Temu/抖音/小红书，含”服饰配件 → 柔和侧光，质感细腻，优雅克制“品类风格
走 ecommerce_product_kit.py 调美图 API，真实出图（非只出 prompt）
需要 DESIGNKIT_OPENCLAW_AK 鉴权
这意味着：用户 docx 要找的”图片生成技能”，我们不是从零没有，而是”有一个通用电商版，缺一个箱包垂直版”。所以回答”文件要不要补”的基准线是——补垂直层，不重写通用层。
三、Q2：文件是否需要补充 / 修改？
3.1 能力对照（docx vs 我们现有资产）
能力维度
docx baigou-bag-ai-vision
我们现有 designkit-ecommerce-product-kit
现有 02_出图提示词 / 提示词工具箱.md
出图方式
只出 prompt（人工+即梦/SD）
直连 API 真实出 7 图
只出 prompt
箱包材质语言
✅ 真皮/人造革/布艺/特殊面料/五金 全表
⚠️ 仅”服饰配件”一句话
部分覆盖
防变形约束
✅ 固定反向负面词
❌ 无
部分
平台合规清单
✅ 抖音/淘宝/小红书/亚马逊 2026
❌ 无
部分
离线 HTML 工具
✅ 移动端一键填充
❌ 无
❌ 无
多宿主 Skill 化
✅ SKILL.md + references
✅ 已是 Skill
❌ 散文档
3.2 结论与已执行动作
结论：需要补充一个”箱包专属视觉技能”层；现有通用层、提示词文档保留并交叉引用即可，不必改。
已在本仓库落地（与 docx 一致，且补齐了被截断的 HTML JS 部分）：
skills/baigou-bag-ai-vision/├── SKILL.md                       # 技能主入口（含触发规则/4步流水线/产能标准/与流水线衔接说明）├── references/│   ├── prompts.md                 # 6+1 提示词体系（6核心+1备用，28+ 模板）│   ├── material-guide.md          # 箱包材质 AI 渲染专用描述手册（11 类材质+3 类五金）│   └── compliance.md              # 2026 四平台合规清单 + 通用自检清单└── assets/    └── baigou-vision-tool.html    # 离线移动端工具（产品参数→7类28模板变量替换+四平台合规+批量改色/视频镜头/亚马逊Listing 三个专项生成器）
建议补改清单（尚未做，待你拍板）：
00_导航索引.md 与 腾讯文档备份索引.md 登记本技能（已可登记，等你确认）。
白沟箱包_可用生图视频提示词工具箱_20260810.md 末尾加”→ 详见 skills/baigou-bag-ai-vision“交叉引用，避免两套提示词各自为政。
V1.0 综合提示词库（白沟箱包定时任务_综合提示词库v4_V2.0整合版.md）若含”出图”章节，应指向本技能作为箱包专用标准源。
离线 HTML 工具可进一步：① 接入 designkit API 一键出图（需 AK）；② 增加”中英双语”切换以服务亚马逊跨境。属于增强项，非必需。
四、Q3：对定时任务有没有参考价值？
4.1 现有定时任务架构（回顾）
主线 5017165（每日 14:00）：T1 情报 → T2 选题 → T6 脚本，T5「只出 prompt 绝不自动出图」（人工 + 即梦/剪翼）。
Track C：4697752（每日 09:00）、4697762（每周一 09:00）独立运行。
4.2 参考价值评估
模块
能否接入定时任务
建议
Step1~Step3 提示词生成（产品解析 + 5 张分镜 + 6+1 提示词）
✅ 能，且强烈建议
T5 当前”只出 prompt”，接入本技能后，prompt 从”通用”升级为”箱包材质精准 + 防变形 + 合规后缀“，质量与返工率直接改善。这是最实在的参考价值。
Step4 合规终审
✅ 能
每日产出图文/视频前，用 compliance.md 做一遍自检（极限词、水印、AI 声明、尺寸），降低平台违规风险。可挂到 T6 后道质检。
HTML 离线工具
⚠️ 有限
定时任务跑在云端无界面，离线 HTML 工具是给人工在手机/电脑上批量出提示词用的，不适合自动调用；但其中的”批量改色/视频镜头/Listing”生成逻辑可提炼成脚本给 T5 用。
真实出图（designkit/即梦 API）
❌ 不应自动跑
违背 T5”绝不自动出图”既定规则；消耗 credits、需人工选风格、易产生违规图。保持”人工触发 + 人工选风格”边界。
一句话：本技能对定时任务的价值 = 让 T5 出更好的 prompt + 给 T6 加一道合规质检；不是把自动出图塞进定时任务。
4.3 与 GitHub 同类技能的差异化定位
GitHub 那几个（buluslan/w-cyh/liangdabiao）本质是”通用电商模板 + 直连 GPT-Image-2 出图”，强调自动出图；而我们白沟场景的纪律是”定时任务只出 prompt、人工出图“。所以：
直接照搬 GitHub 的”出图脚本”进定时任务 ❌ 不符合我们的运营纪律。
借鉴其”25 模板 / 模板智能匹配 / 参考图一致性 / 反 AI 感”的思路，喂给我们已有的 designkit 人工出图环节 ✅ 合理。
五、下一步建议（待你确认后执行）
登记索引：把 skills/baigou-bag-ai-vision 写入 00_导航索引.md 与腾讯文档备份索引（含 file_id 权威标识）。
交叉引用：在 白沟箱包_可用生图视频提示词工具箱_20260810.md 与 V1.0 提示词库加指向本技能的链接，形成”箱包出图唯一标准源”。
可选增强：HTML 工具加中英双语 / 接 designkit API；把”批量改色、视频镜头、Listing”逻辑抽成脚本供 T5 调用。
保持纪律：定时任务仍坚持”只出 prompt、人工出图”，合规清单作为 T6 后道质检挂上。
附：本次新增文件清单
文件
说明
skills/baigou-bag-ai-vision/SKILL.md
技能主入口（含与流水线/定时任务的衔接说明）
skills/baigou-bag-ai-vision/references/prompts.md
6+1 提示词库（28+ 模板）
skills/baigou-bag-ai-vision/references/material-guide.md
箱包材质语言手册
skills/baigou-bag-ai-vision/references/compliance.md
2026 四平台合规清单
skills/baigou-bag-ai-vision/assets/baigou-vision-tool.html
离线移动端工具（已补完 JS，可离线用）
箱包AI视觉技能_同类调研与整合建议_20260812.md
本报告

