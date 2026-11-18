# 言井俄语选题库 V0.2

## 用途与边界

本库按“问题母题 → 内容方向 → 实际节目索引”组织，另以全局共享讲解切入点建立横向关联。用途是持续积累值得开发的俄语表达问题、按可观察困难分类、管理不同切入方向、识别跨分类共享切入点、审查与历史内容的实质重合、判断独立制作价值，并记录方向已采用与后续可开发情况。

**当前适用栏目仅为《说不出俄语那点事儿》**，主要面向一般俄语学习者，讨论广义的语言输出、交流困难和相关学习心态。本库不是商务俄语栏目的选题库，不将商务任务分析混入当前问题母题。

本库不承担视频制作档案库功能，不保存完整台本、分镜、视频素材、剪辑工程或制作交接材料。节目表只保存选题覆盖范围、练习与学习收获及可核实的进度摘要。

## 当前文件与唯一数据来源

| 文件 | 职责 |
| --- | --- |
| [problems.csv](problems.csv) | 问题母题及可观察困难分类 |
| [shared_angles.csv](shared_angles.csv) | 全局共享讲解切入点 |
| [directions.csv](directions.csv) | 母题下的内容方向、共享关联、差异审查及开发／复用状态 |
| [episodes.csv](episodes.csv) | 实际节目、关联方向、教学覆盖范围及进度 |
| [TOPIC_TREE.md](TOPIC_TREE.md) | 从四张权威 CSV 自动生成的浏览视图 |
| README.md | 编号、分类、维护、校验与生成规则 |

节目通过 `episodes.direction_id` 关联方向；母题及共享切入点均从方向关联查询，不在节目表重复维护其外键。不在方向表保存手工节目列表，同一方向可关联多期节目。原详细 `episodes/EP001.md` 已移除，必要的教学覆盖与进度已迁入 CSV；旧版本可查 Git 历史。

## 分类、编号与关联含义

| 编号／字段 | 含义与约束 |
| --- | --- |
| A / B / C / D | 已讨论确定的一级困难分类：启动困难／组织困难／展开困难／应变困难；是可观察输出困难的归档入口，不代表严格先后四阶段 |
| A1 | 已实际入库使用的二级分类：A 下的“找不到表达起点”；其他二级工作分类已讨论确定，但暂无对应母题记录 |
| P001 | 全库唯一问题母题 ID，数字独立递增；主分类挂靠一级／二级困难分类 |
| P001-D01 | P001 下的内容方向；D01 在该母题内递增，每个方向必须关联一个主要母题 |
| G001 | 全局共享切入点 ID，数字独立递增；连接跨母题或跨分类的实质相同讲解切入点 |
| EP001 | 实际节目 ID，数字独立递增；不因策划完成而视为已经制作或发布 |
| scene_tags | 独立场景标签，如日常闲聊、开放式提问；不构成分类层级 |

主链为 `A → A1 → P001 → P001-D01 → EP001`。G 编号不插入树形主链；它从方向横向关联。共享 G 不等于同一困难分类，也不等于节目重复。仅场景、举例或练习形式相同，不足以自动认定同一讲解切入点。

B、C、D 的首轮二级工作分类已完成讨论，定义和适用边界见下节；**已审定分类不等于已有母题记录**。分类依据可观察的输出困难，不能直接按使用场景、教学方法或推测原因归类。若新提案的归属不清，须注明待审定并提醒用户，不静默重分类或增加未经讨论的新类别。

编号在各自命名空间内唯一、稳定，不因封存回收或重用。A1 下可以有多个母题，但同一个母题不在多个一级分类下重复创建。分类调整须先说明影响、保留历史映射并检查引用；不得静默改写历史 EP 的教学覆盖。

## 分类基准与二级工作分类（2026-11-18 讨论结论）

> **必留分类原则备注：** 一级及二级分类以学习者在实际交流／表达中**可观察、可描述的外在输出困难**为主要判断依据；不能将推测的心理活动、思维方式、词汇／语法加工机制或教学技巧直接当成分类定义。同一种外在困难可能有不同原因；本期成因解释与教学干预，应在具体方向／单集开发时论证，不默认适用于整个母题。

| 一级 | 二级编号 | 二级名称 | 观察与归类重点 |
| --- | --- | --- | --- |
| A 启动困难 | A1 | 找不到表达起点 | 需要开始表达时，迟迟无法形成第一步可说的内容；既可能发生于开启对话，也可能发生于开始一次个人讲述 |
| B 组织困难 | B1 | 信息呈现顺序不清 | 多个信息已经表达，但时间、事件发展或叙述推进的线索不足，使听者难以追踪排列关系 |
| B 组织困难 | B2 | 信息逻辑关系不清 | 信息点已表达，但因果、转折、条件、主次等逻辑／语义关系交代不清 |
| C 展开困难 | C1 | 表达缺乏具体化 | 主要信息基本可理解，但在当前交流任务需要时，难以进一步给出足够具体的描述、理由或例子 |
| C 展开困难 | C2 | 关键支撑信息缺失 | 已有初步表达，但缺少理解事件发展或支撑主要结论所必需的关键信息环节 |
| D 应变困难 | D1 | 追问后难以接续 | 初始交流能够进行，但遇到进一步追问时无法及时接续回应 |
| D 应变困难 | D2 | 非预期回应下难以调整 | 对方提出意外反馈、异议或纠正后，难以调整回应以继续交流 |
| D 应变困难 | D3 | 理解不确定时难以修复交流 | 没听清、没理解或不确定理解是否正确时，难以请求重复、澄清、确认并继续互动 |

**层级与交叉关系。** A/B/C 聚焦输出本身的启动、组织、展开表现；D 聚焦实时互动中受到追问、变化或理解不确定性影响时的应答／修复表现。四类不是严格顺序，也不要求互斥；A/B/C 的困难可能出现在 D 所描述的互动条件下。根据本次选题主要解决的**外在困难**确定一个主分类，其他有关联的困难作为备注／关联线索记录，不为同一母题重复建立多个 P。B/C 也不限于事件叙述；观点解释和事物介绍同样可能遇到组织、展开问题。

**B1 与 B2 的边界。** B1 侧重听者能否追踪信息的**排列、时间和推进线索**；B2 侧重听者能否识别**已表达信息之间的逻辑／语义关系**。两者可能共现，仍可针对不同外在表现分别开发方向。倒叙、插叙、个性化表达或仅有个别听者没听懂，不自动构成表达能力不足；应结合交际目的、听者背景与必要组织线索判断，不能仅凭表达风格推断缺陷。

**C1 与 C2 的边界。** C1 是主要信息已经成立，但在任务确实需要时**具体化不足**；C2 是理解主线／结论所必需的**关键支撑内容未说出**。两者并非固定的先后学习阶段，也不因句子短、没讲完全部细节就自动判为困难。C2 与 B2 的区分：C2 的关键内容**缺席**；B2 的相关信息**已经说出，却未交代清楚彼此关系**。判断必须结合当时交流任务与信息交换目标。

**D 类与输入能力的边界。** 本栏目不以听力、阅读能力专项作为独立主体选题。但理解不足或不确定，可能触发可观察的**应答／交流修复困难**；请求对方重复、澄清与核对理解属于 D3 可开发的输出／互动策略，尤其适用于初学者。D1、D2、D3 的外在触发条件不同，允许交叉，不能把“听不懂”本身当成 D3 的全部定义。

**表达任务与呈现情境。** 暂不新增“表达任务形态”这一独立数据库字段。需要时在具体选题的情境讨论与既有 `scene_tags`／`example_scene` 中表达；“表达任务”与视频最终叙事情境有关但不等同，不能为区分 A/B/C/D 而额外制造长期维护字段。

**实施边界。** 此表是已经讨论通过的分类**工作基准**，不是对 B1—D3 各自建立了新母题或新节目。当前四张 CSV 仍只保留已确证的 P001、P001-D01、G001、EP001；不为填满目录创造虚构 P、方向或 EP。自动生成的选题树仅展示有真实记录的节点，未显示 B/C/D 不构成数据缺失或错误。分类可在选题实践中经审定后调整，不随意静默更名或迁移历史记录。

## CSV 字段与维护约定

统一使用 UTF-8、英文小写蛇形字段名、标准逗号分隔；包含逗号、引号或换行的值按 CSV 规范引用。多场景标签、多匹配编号或多发布链接用 `|` 分隔。未知字段留空或明确标注待核实；主键、主要母题及实际节目的方向外键不得缺失。未确认的共享切入点关联可留空，树中显示待确认。

- **problems.csv**：`problem_id` 为主键；`category_l1_code/name`、`category_l2_code/name` 为分类；`problem_description` 为可观察困难；另有 `scene_tags`、`source_type`、`problem_status`、`notes`。母题长期保留，不因视频发布删除。
- **shared_angles.csv**：`shared_angle_id` 为主键；`shared_angle_name` 为名称；`explanation_focus` 说明核心讲解共同点；`scope_notes` 记录适用边界及限制。没有确认依据不自动新增正式 G 编号。
- **directions.csv**：`direction_id` 为主键，`problem_id` 为必填主要母题外键，`shared_angle_id` 为可选共享外键；`angle`、`example_scene` 描述方向；`historical_difference`、`standalone_rationale` 记录历史差异与独立制作理由；`review_result`、`matched_ids`、`review_reason` 记录查重初判、匹配的已有 P／方向／G／EP 编号及理由；`analysis_status` 区分候选与已形成的本期分析；另含三个独立方向状态字段及 `notes`。
- **episodes.csv**：`episode_id` 为主键，`series_name`、`title` 为栏目与标题，`direction_id` 为必填外键；`core_observation`、`core_explanation`、`explanation_limits`、`content_scope`、`exercise_summary`、`learning_takeaway` 支持教学内容查重；`workflow_status`、`progress_notes`、`publication_status`、`published_at`、`publication_links` 记录真实进度和待核实发布信息；`source_type` 说明依据。原因和练习是本期采用的分析，不自动推广为整个母题的通用教学结论。

## 状态彼此独立

- 母题：`problem_status`，如活跃／归档；归档不删除母题或编号。
- 方向开发：`development_status`，如候选／待论证／可开发／已采用／暂缓。
- 方向复用：`reuse_status` 为开放／封存，封存必须填写 `closure_reason`。有新依据可重新开放，在备注保留原封存理由、重开依据和变更记录；重新开放后当前 `closure_reason` 留空，Git 历史保留原值。
- 节目：`workflow_status` 独立反映每期已知制作进展；`publication_status`、日期及链接另外核实。策划、录制、交付、审核和发布不是同一节点。待核实不等于已确认未发布，也不得据此标为已发布。

封存的是方向，不是节目制作进度；封存方向时，不批量修改历史节目的 `workflow_status`。树只显示“所属方向”状态。已采用不表示已用完，首次方向保持开放。

## 新增方向前的跨分类查重

先读取最新 GitHub 权威数据，不能只依赖标题、关键词、场景或聊天记忆。每次同时检索：

1. 相同或相近母题的可观察困难及其已有方向，区分场景变化与困难变化。
2. 不同分类下的 G 共享切入点及关联方向，比较核心讲解共同点。
3. 已有实际节目的核心解释、覆盖范围、练习及学习收获，并结合真实进度区别已规划内容与已确认发布内容。

逐项回答：是否有实质性表达困难或切入角度差异？能否提供此前未充分覆盖的教学价值？为什么值得独立制作，而不是作为旧内容的例子或补充？

将“高度重复／共享切入点但可能独立／具有新价值”的初步判断写入 `review_result`，在 `matched_ids` 和 `review_reason` 留下匹配编号与依据，并填写历史差异及独立理由。尚未完成教学分析的候选方向在 `analysis_status` 标为待论证，不能把初判当成教学结论成立。首次基线无匹配可留空，但须说明检索边界。

读取失败必须明确说明没有完成全库查重。高度重复的提案先向用户解释重合与影响，不自动创建正式新方向；有实质差异的提案也须有证据，不能只因换了场景便认定新价值。

## 分类冲突处理

新增或修改违反关系时，先提醒用户并说明影响，待消除疑义后操作。特别检查：把场景变化当成新困难；因相同练习错误合并不同困难；在多个一级分类重复建立同一母题；把方向封存写成历史节目状态变化；凭空创建未审定二级编号。分类、共享关联或封存理由存在争议时，保留待审定，不静默改变归属。

## 当前首次归档

实际记录仅有 P001、P001-D01、G001、EP001。P001 为 A／A1 下的启动困难，方向聚焦开放式问题下的话题与起点选择；G001 暂名“通过具体自我提问缩小表达任务”，当前只关联该方向，不虚构其他母题或节目。

EP001 保留：具体问题与开放式问题的观察对照；话题选择、起点规划和俄语组织可能共同形成负担的解释及限制；先选一件事、具体自我提问以尝试形成第一句话的练习。内容策划基本定稿、真人已录制；实际制作交付、成片审核及发布情况待核实，不标记为已发布。日期和发布链接留空。

## 与商务俄语栏目的内容边界（暂定，待商务首期另行审定）

- **当前栏目《说不出俄语那点事儿》：** 面向较广泛的俄语学习者，主要讨论语言输出、真实交流中的表达困难及相关学习心态；着重语言表达形式，不深入分析某个行业业务。日常、社交及一般学习场景优先；工作／商务背景可少量作为辅助情境，但应尽量少用，不把该背景中的业务思维当成本栏目的教学主体。此前讨论过约 1/5—2/5 的低占比参考范围，**并未批准为硬性数量配额**，实际以选题适配性优先。
- **商务俄语栏目：** 是独立的策划与内容体系，面向真实商务沟通需求者，可能涉及商务任务、商务思维、商务心理及俄语表达。**不能直接复用本栏目 A/B/C/D 分类为商务栏目的正式分类，更不能把商务选题混入本栏目 P／方向／EP。**
- 当前库的 G 编号只是**本栏目内部**跨母题、跨分类的横向检索关系，不能自动扩展为跨栏目的统一共享编号。未来如需跨栏目检索或内容差异审查，应在商务栏目第一期完成后，单独确定双方的归档范围、关联规则及编号空间。
- 即便两栏目的情境或语言表达技巧表面相似，也不能直接认定内容重复；应先分别核对受众、任务目标和内容价值。不得为尚未开展的商务首期制造未验证的分类、母题或节目记录。

## 本轮暂停节点与下次内容填充任务

截至 2026-11-18，**已完成 A/B/C/D 分类边界及 A1、B1、B2、C1、C2、D1、D2、D3 八项二级工作分类的讨论审定**；同时确认可观察输出困难原则、A/B/C 与 D 可交叉、D3 的交流修复边界、以及两栏目独立管理。

**尚未完成：** 在二级分类下筛选首批具体问题母题、为每个母题提出 1—2 个有独立价值的候选内容方向、记录可能的解释切入点及待验证教学机制、与 EP001／已有 G 的实质去重、挑选下一期优先制作方向。**以上全部标记为下次选题会待办，不预先创建数据行。**

下次恢复时：先按已审定的外在表现标准提出候选 P，再审查内容方向独立成片价值；不要因为本轮已经确定分类，就自动填入未讨论确认的母题或教学原因。更新 CSV 后才依 README 生成树状索引。

## 树状浏览、生成与核验

TOPIC_TREE.md 是四张 CSV 的派生视图，不人工维护第二份数据。两个入口分别为“一级 → 二级 → 母题 → 方向 → 节目”和“G → 关联母题／方向 → 节目”；只显示实际入库记录，缺失分类或共享关联显示待确认，不填充虚构节点。维护 CSV 后须重新生成，并与 CSV 一起提交。

在仓库根目录使用 Node.js 执行以下命令，可用同一生成逻辑重建视图（不需要安装依赖）：

```sh
node <<'JS'
const fs = require("node:fs");
const path = require("node:path");
function parseCSV(s){let rows=[],row=[],cell="",q=false;for(let i=0;i<s.length;i++){let c=s[i];if(c==='"'){if(q&&s[i+1]==='"'){cell+='"';i++;}else q=!q;}else if(c===","&&!q){row.push(cell);cell="";}else if(c==="\n"&&!q){row.push(cell);rows.push(row);row=[];cell="";}else if(c!=="\r"||q)cell+=c;}if(q)throw Error("CSV引号未闭合");if(cell||row.length){row.push(cell);rows.push(row);}if(rows.some(r=>r.length!==rows[0].length))throw Error("CSV列数不一致");return rows.slice(1).map(r=>Object.fromEntries(r.map((v,i)=>[rows[0][i],v])));}
function renderTree(t){
 const sort=a=>[...a].sort((a,b)=>String(Object.values(a)[0]).localeCompare(String(Object.values(b)[0]),"en"));
 const safe=s=>String(s||"待确认").replace(/\r?\n/g," ").replace(/</g,"&lt;").replace(/>/g,"&gt;");
 const line=(n,s)=>"  ".repeat(n)+"- "+s;
 const epLines=(d,n)=>{const es=sort(t["episodes.csv"].filter(e=>e.direction_id===d.direction_id));return es.length?es.map(e=>line(n,`${safe(e.episode_id)}｜${safe(e.title)}｜制作：${safe(e.workflow_status)}｜发布：${safe(e.publication_status)}｜所属方向：${safe(d.reuse_status)}`)):[line(n,"暂无关联节目（不代表已制作）")];};
 const dirLines=(d,n)=>[line(n,`${safe(d.direction_id)}｜${safe(d.angle)}｜开发：${safe(d.development_status)}｜复用：${safe(d.reuse_status)}｜共享切入点：${safe(d.shared_angle_id)}${d.closure_reason?"｜封存理由："+safe(d.closure_reason):""}`),...epLines(d,n+1)];
 const out=["# 选题树 V0.2","","<!-- 自动生成：权威来源为 problems.csv、shared_angles.csv、directions.csv、episodes.csv。禁止手改；再生成方法见 README.md。 -->","","## 按问题分类",""];
 const ps=sort(t["problems.csv"]),ds=sort(t["directions.csv"]),gs=sort(t["shared_angles.csv"]);
 const l1s=[...new Set(ps.map(p=>p.category_l1_code))].sort();
 for(const l1 of l1s){const group=ps.filter(p=>p.category_l1_code===l1);out.push(line(0,`${safe(l1)}｜${safe(group[0].category_l1_name)}`));
 for(const l2 of [...new Set(group.map(p=>p.category_l2_code))].sort()){const sub=group.filter(p=>p.category_l2_code===l2);out.push(line(1,l2?`${safe(l2)}｜${safe(sub[0].category_l2_name)}`:"二级分类待审定"));
 for(const p of sub){out.push(line(2,`${safe(p.problem_id)}｜${safe(p.problem_description)}｜${safe(p.problem_status)}`));const dirs=ds.filter(d=>d.problem_id===p.problem_id);for(const d of dirs)out.push(...dirLines(d,3));if(!dirs.length)out.push(line(3,"暂无内容方向"));}}}
 out.push("","仅展示 CSV 中实际入库的分类和记录；其他一级类别暂无母题，未审定的二级分类不自动创建。","","## 按共享讲解切入点","");
 for(const g of gs){out.push(line(0,`${safe(g.shared_angle_id)}｜${safe(g.shared_angle_name)}`));const dirs=ds.filter(d=>d.shared_angle_id===g.shared_angle_id);for(const pid of [...new Set(dirs.map(d=>d.problem_id))].sort()){const p=ps.find(p=>p.problem_id===pid);out.push(line(1,`${safe(pid)}｜${safe(p?.category_l1_code)}／${safe(p?.category_l2_code)}｜${safe(p?.problem_description)}`));for(const d of dirs.filter(d=>d.problem_id===pid))out.push(...dirLines(d,2));}if(!dirs.length)out.push(line(1,"暂无关联方向，待确认"));}
 const unlinked=ds.filter(d=>!d.shared_angle_id);if(unlinked.length){out.push("","### 共享切入点关联待确认","");for(const d of unlinked)out.push(...dirLines(d,0));}
 out.push("","共享 G 编号是横向关联，不改变母题分类，也不自动判定节目重复。","");
 return out.join("\n");
}
const root = "marketing/content_system/topic_library";
const names = ["problems.csv", "shared_angles.csv", "directions.csv", "episodes.csv"];
const data = Object.fromEntries(names.map(name => [name, parseCSV(fs.readFileSync(path.join(root, name), "utf8"))]));
fs.writeFileSync(path.join(root, "TOPIC_TREE.md"), renderTree(data), "utf8");
JS
```

提交前验证 UTF-8 和字段、主键唯一、外键有效、方向编号前缀、分类合法、封存理由、制作与发布状态、树与 CSV 一致及变更范围。只修改本库，不覆盖课程、招聘或技术资料。
