# Local Health Records

Use this reference only when the user explicitly asks to maintain persistent health information and the current environment allows local file read/write.

## Principle

Health records are sensitive. Do not create, update, or infer persistent records silently.

Before the first write, ask or confirm:

“我可以在本地维护一个 Markdown 健康档案，后续咨询时用来减少上下文断层。这个档案可能包含身高、体重、疾病、饮食、运动和家人信息。是否要记录？”

If the user agrees, use local Markdown files.

## Recommended Paths

Default private path inside a project:

```text
health-records/
  README.md
  self.md
  people/
    father.md
    mother.md
    child.md
  daily/
    2026-05.md
```

Important:

1. Add `health-records/` to `.gitignore`.
2. Do not commit real health records.
3. If the user chooses another path, follow the user’s path.

## File: self.md

Use this structure:

```markdown
# 健康档案：本人

> 私人健康信息。不要上传到公开仓库。

## 基本信息

- 姓名/称呼：
- 性别：
- 出生年份/年龄：
- 身高：
- 当前体重：
- 目标体重/目标：
- 记录更新时间：

## 身体状况

- 已明确诊断：
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

## 咨询偏好与限制

- 饮食偏好：
- 忌口/不吃：
- 做饭条件：
- 预算/便利性：
- 最难执行的地方：

## 最近问题

- 

## 待确认信息

- 

## 更新记录

- YYYY-MM-DD：
```

## Related People

For family members or other people, create one file per person under `health-records/people/`.

Use non-identifying filenames when appropriate, such as:

```text
people/father.md
people/mother.md
people/spouse.md
people/client-a.md
```

Structure:

```markdown
# 健康档案：称呼

> 私人健康信息。不要上传到公开仓库。

## 关系与基本信息

- 与咨询者关系：
- 称呼：
- 性别：
- 出生年份/年龄：
- 身高：
- 当前体重：
- 记录更新时间：

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

## Daily Records

Use monthly files for lightweight logs:

```markdown
# 日常记录：YYYY-MM

## YYYY-MM-DD

### 饮食

- 早餐：
- 午餐：
- 晚餐：
- 加餐/饮料：
- 总热量估计：
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
- 备注：
```

## Update Rules

When new information appears:

1. Identify whose record it belongs to: self, father, mother, spouse, child, client, etc.
2. Update stable facts in the person profile.
3. Update daily data in the monthly log.
4. Put uncertain information under “待确认信息”.
5. Do not overwrite old diagnoses or important values without preserving date context.
6. Add an entry under “更新记录”.

## Before Giving Advice From Records

Say briefly:

“我会参考你本地档案里的信息，但如果身高体重、诊断、用药或检查结果有变化，需要先更新。”

Then proceed with normal safety boundaries.

## Privacy

Never print the full health record unless the user asks.

When summarizing, include only information relevant to the current question.

Never commit, upload, or share `health-records/` unless the user explicitly asks and confirms privacy implications.
