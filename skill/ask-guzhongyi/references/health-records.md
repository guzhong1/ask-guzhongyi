# Local Health Records

Use this reference only when the user’s question involves personal or family health information, daily records, follow-up context, or an explicit request to remember/update information, and the current environment supports local file read/write.

## Product Intention

The health record is part of the personal and long-term consultation experience, not an afterthought. It is not needed for every general science question.

Its purpose is to prevent context loss across conversations by keeping a clear, human-readable Markdown record of:

1. The user’s basic body status and diagnoses.
2. Daily diet, calorie estimates, exercise, symptoms, and lifestyle data.
3. Related people such as parents, spouse, children, or other consultation targets.

The format must be easy for ordinary users to open and understand.

## Trigger Judgment

Do not mention local health records when the user asks general questions such as:

1. “晚上吃碳水会胖吗？”
2. “维生素 D 有必要补吗？”
3. “咖啡空腹喝伤胃吗？”
4. “蛋白粉是不是智商税？”

Consider asking whether to create or update a local health record when the user provides personal or family information, such as:

1. Height, weight, body fat, waist circumference.
2. Diagnoses, symptoms, medication, allergies, test results.
3. A daily meal, calorie estimate, exercise amount, sleep, weight record.
4. Family member or related-person information.
5. Long-term goals such as weight loss, blood sugar control, lipid control, or repeated follow-up.

Suggested transition:

“你这个问题已经涉及个人情况。如果你打算之后持续咨询，我可以帮你在本地建立一个 Markdown 健康档案，记录身高、体重、诊断、饮食、运动等信息，之后就不用每次重新说一遍。需要我建立吗？”

## Privacy Message

When personal information appears and no local record exists, explain:

“你这个问题已经涉及个人情况。长期做营养健康咨询时，最好在本地留一个 Markdown 健康档案。这样以后再问，我可以直接参考你之前记录过的身高、体重、疾病、饮食、运动和家人情况，减少上下文断层。这个档案会保存在你电脑本地的 `health-records/` 文件夹里，本 Skill 不会把它上传到云端。是否要现在帮你建立？”

Only create the first record after the user agrees.

After creating or updating records, say:

“我已经把这次信息记录到本地 `health-records/` 文件夹下了。以后你再咨询时，我可以参考这些本地 Markdown 档案。它们保存在你的本地电脑上，本 Skill 不会上传到云端。”

If the tool cannot write local files, say:

“当前工具环境看起来不能直接写入本地文件。你可以手动创建 `health-records/` 文件夹，并按我给你的 Markdown 模板保存。”

## Directory Layout

Default path:

```text
health-records/
  README.md
  self.md
  people/
    father.md
    mother.md
    spouse.md
    child.md
  daily/
    2026-05.md
```

Rules:

1. Add `health-records/` to `.gitignore`.
2. Do not commit real health records.
3. Keep filenames simple, stable, and non-sensitive.
4. If the user chooses another local path, follow the user’s path.

## README.md Template

Create `health-records/README.md`:

```markdown
# 本地健康档案说明

这个文件夹用于保存营养健康咨询中的本地 Markdown 档案。

这些文件保存在你的本地电脑上，不应该上传到 GitHub 或其他公开平台。

## 文件说明

- `self.md`：本人基本健康档案
- `people/`：家人或其他咨询对象的健康档案
- `daily/`：按月份保存的饮食、运动、体重、症状等日常记录

## 使用提醒

1. 每次咨询前，如果身高、体重、诊断、用药、检查指标有变化，请先更新。
2. 涉及疾病营养建议时，应先有医生的明确诊断。
3. 急症或持续加重症状，请直接线下就医或急诊评估。
```

## self.md Template

Create `health-records/self.md`:

```markdown
# 健康档案：本人

> 私人健康信息。保存在本地电脑，不要上传到公开仓库。

## 一句话概览

- 当前目标：
- 主要健康关注：
- 最近更新时间：

## 基本信息

- 称呼：
- 性别：
- 出生年份/年龄：
- 身高：
- 当前体重：
- 目标体重/目标：
- 腰围/体脂率：

## 身体状况

- 已明确诊断：
- 疑似但未明确诊断：
- 重要既往史：
- 过敏史：
- 当前用药：
- 当前补充剂：
- 重要检查指标：

## 日常数据

- 饮食总热量估计：
- 蛋白质摄入估计：
- 饮食结构备注：
- 运动量：
- 睡眠：
- 压力/工作节奏：

## 饮食偏好与现实限制

- 饮食偏好：
- 忌口/不吃：
- 做饭条件：
- 外食情况：
- 预算/便利性：
- 最难执行的地方：

## 最近咨询问题

- 

## 待确认信息

- 

## 更新记录

- YYYY-MM-DD：
```

## Related Person Template

Create one file per related person under `health-records/people/`.

Examples:

```text
people/father.md
people/mother.md
people/spouse.md
people/child.md
```

Template:

```markdown
# 健康档案：称呼

> 私人健康信息。保存在本地电脑，不要上传到公开仓库。

## 一句话概览

- 与咨询者关系：
- 主要健康关注：
- 最近更新时间：

## 基本信息

- 称呼：
- 性别：
- 出生年份/年龄：
- 身高：
- 当前体重：
- 目标/主要诉求：

## 身体状况

- 已明确诊断：
- 疑似但未明确诊断：
- 重要既往史：
- 过敏史：
- 当前用药：
- 当前补充剂：
- 重要检查指标：

## 日常数据

- 饮食情况：
- 运动量：
- 睡眠：
- 近期症状时间线：

## 就医沟通

- 已看科室/医生：
- 医生意见：
- 待问医生的问题：
- 下次复诊/检查：

## 待确认信息

- 

## 更新记录

- YYYY-MM-DD：
```

## Daily Monthly Log Template

Use `health-records/daily/YYYY-MM.md`:

```markdown
# 日常记录：YYYY-MM

## YYYY-MM-DD

### 饮食

- 早餐：
- 午餐：
- 晚餐：
- 加餐/饮料：
- 总热量估计：
- 蛋白质估计：
- 结构观察：

### 运动

- 类型：
- 时长：
- 强度：
- 步数/消耗估计：

### 身体状态

- 体重：
- 症状：
- 睡眠：
- 情绪/压力：
- 备注：
```

## Automatic Update Rules

After initialization, when the user provides new personal or family health information during normal consultation, update the local record without asking every time, as long as it is clearly relevant and the user has not opted out.

Update these categories:

1. Stable body facts: height, weight, diagnoses, allergies, medication, supplements, key test results.
2. Daily data: meals, calorie estimates, protein estimates, exercise, sleep, symptoms.
3. Related people: names/labels, relationship, body status, diagnoses, symptoms, doctor opinions.
4. Context: goals, constraints, preferences, execution difficulties.

Do not infer uncertain medical facts. Put uncertain items under “待确认信息”.

Do not overwrite old important values without date context. Add a dated update record.

## Reply After Update

After updating records, keep the note short:

“我已经把这次信息记录到本地 `health-records/self.md` 和 `health-records/daily/YYYY-MM.md` 里了。以后再问时，我可以直接参考这些本地档案；它们保存在你的电脑上，本 Skill 不会上传到云端。”

For related people:

“我已经把这次信息记录到本地 `health-records/people/father.md` 里了。以后再问你父亲相关问题时，我可以参考这份本地档案；它保存在你的电脑上，本 Skill 不会上传到云端。”

## Using Existing Records

Before giving advice based on records, say briefly:

“我会参考你本地档案里的信息；如果身高体重、诊断、用药或检查结果有变化，需要先更新。”

Then follow normal safety boundaries.

## User Controls

Respect these requests:

1. “不要记录”：stop updating persistent records.
2. “删除我的档案”：delete the relevant local Markdown files if the environment permits.
3. “给我看档案”：show the relevant file or a concise summary.
4. “导出档案”：provide the Markdown content or path.

## Privacy

Never print the full health record unless the user asks.

When summarizing, include only information relevant to the current question.

Never commit, upload, or share `health-records/` unless the user explicitly asks and confirms privacy implications.
