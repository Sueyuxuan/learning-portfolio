# Learning Git Properly: From Uploading Files to Recording Progress

> 这是一篇学习反思，不是 Git 教程。
> 记录的是我在完成 Kaggle 入门学习之后，回头发现自己一开始就误解了 GitHub 的过程。

---

## 1. Why I Started Thinking About Git Again

我最早接触 GitHub，是因为在学 Python 和数据分析。

那段时间我完成了 Kaggle 的三个入门课程：Intro to Programming、Python、Pandas。每学完一部分，我会把笔记整理成 Markdown 文件，然后想办法放到 GitHub 上。当时的动机很简单——我希望这些笔记不要只躺在自己电脑的某个文件夹里，希望它们在一个"看得见"的地方。

所以我装了 GitHub Desktop，建了一个 `learning-portfolio` 仓库，开始往里面放文件。

现在回头看，我在那几周里做过很多次 commit，但我几乎没有想过 commit 是什么。我关心的只有一件事：

> 文件有没有成功传上去？

这个阶段持续了挺久，一直到最近我开始准备一个正式的研究项目（一个关于旅游增长与地方经济的数据分析项目）。当我在想"这个新仓库要怎么组织"的时候，我第一次认真去看了自己 `learning-portfolio` 的 commit history。

然后我发现，那段历史我自己都读不懂。

一整列的 `update`、`add notes`、`day 3`、`modify`。我知道那几周我确实学了东西，但从这些记录里，我看不出**哪一天学了什么、哪一次修改是在纠正之前的错误、我在哪个点上卡住过**。

那一刻我意识到，我之前理解的 GitHub，和 GitHub 真正在做的事，可能不是一回事。

这篇笔记就是为了把这个认识写下来。

---

## 2. My First Misunderstanding of GitHub

我最初对 GitHub 的理解，用一句话概括就是：

> GitHub = 一个可以放代码和笔记的在线文件夹。

也就是说，我把它当成了云盘。

我现在觉得，这个误解几乎是必然的，而且不完全是因为我懒或者不认真。有几个具体原因：

**第一，初学者的注意力会被"看得见的结果"完全占据。**

刚开始用 GitHub Desktop 的时候，我脑子里全是这些问题：文件夹路径对不对？为什么我建的空文件夹在网页上看不见？README 怎么显示成一堆 `#` 号了？Publish 按钮点了之后为什么没反应？

这些问题都有一个共同点——**它们会立刻给你反馈**。做错了，网页上就是不对；做对了，刷新一下就能看到文件。所以我的全部精力都花在解决这类问题上。

**第二，写不好 commit message，当下不会有任何惩罚。**

这是我认为最关键的一点。

如果我把文件放错了目录，我马上就会发现。但如果我在 Summary 里写了一个 `update`，会发生什么？

什么都不会发生。文件照样上传成功，网页照样正常显示，GitHub 不会报错，也不会提醒我。

**一个不会立刻出问题的错误，初学者是察觉不到的。**它的代价被推迟了——推迟到三个月以后，推迟到我需要回头查"我是什么时候改的这个"的那一天。而那时候，代价已经无法弥补了。

**第三，我当时的使用场景，确实"不需要"commit。**

我那时候的工作方式是：写完一篇笔记 → 保存 → 打开 GitHub Desktop → 全选 → 随便写点什么 → Commit → Push。

在这个流程里，commit 只是"上传"这个动作中间必须点的一个按钮。它没有别的意义，因为我从来没有回头看过历史，也从来没有需要过。

我现在会把这个阶段叫做**"把 GitHub 当云盘"阶段**。我猜大部分自学的人都会经过这个阶段。问题不在于经过它，而在于会不会走出来。

---

## 3. What a Commit Actually Means

我试着用现在能理解的方式重新说一遍。

### 最简单的说法

> Commit 就像给项目当前的状态拍了一张照片，并且在照片背面写了一句说明。

照片记录的是"这一刻，我的所有文件长什么样"。背面那句说明，就是 commit message。

### 再往前一步

一次 commit 通常意味着：

> "我刚完成了一个相对完整的小修改，现在我要把这个状态记录下来。"

注意这句话里的两个词：**完整**和**小**。

- **小**：不是把三天的工作攒在一起提交；
- **完整**：也不是改了半句话就提交。

它是一个"能用一句话说清楚"的工作单位。这个判断标准我在第 5 节会展开。

### commit 到底记住了什么

我之前以为 commit 只是存了个文件。实际上一次 commit 至少记录了这些东西：

| 记录的内容 | 我以前的理解 | 实际情况 |
|---|---|---|
| 哪些文件被改了 | 没想过 | 精确到每一个文件 |
| 每个文件里具体改了哪几行 | 完全不知道 | 逐行记录，可以对比查看 |
| 谁做的修改 | 没想过 | 提交者姓名和邮箱 |
| 什么时候改的 | 以为只有"最后修改时间" | 精确到秒的时间戳 |
| 为什么改 | **这一项我丢掉了** | 就是 commit message |
| 和上一个版本的关系 | 没有这个概念 | 每个 commit 都指向它的上一个 commit |

最后两行是我以前完全没有的概念。

第五行"为什么改"——这是 Git 唯一无法自动记录、只能由我自己写下来的东西。Git 能自动知道我改了哪一行，但它永远不知道我为什么要改。**那句话如果我不写，就永远丢了。**

第六行"和上一个版本的关系"——这意味着所有 commit 不是一堆散落的文件备份，而是**一条链**。正是这条链构成了"项目的历史"。

### 稍微正式一点的定义

用比较标准的说法：

> 一个 commit 是版本库中的一个不可变的快照，它记录了某一时刻项目所有被追踪文件的完整状态，包含作者、时间、说明信息，以及指向其父提交的引用。所有 commit 通过父子关系连接，构成项目的完整历史。

这个定义我现在读得懂了，但如果三个月前有人这样跟我说，我大概率还是会继续写 `update`。所以我把简单的说法放在前面。

---

## 4. Save vs Commit vs Push

这三个词我以前是混着用的，现在能分清了。

### Save（保存）

> 保存 = 把我在编辑器里改的内容写进硬盘上的那个文件。

例子：我在 `python_learning_notes.md` 里补了一段关于 for loop 的理解，然后按 `Ctrl + S`。

这时候发生的事：硬盘上那个文件的内容变了。仅此而已。

Git 完全不在乎这件事。GitHub Desktop 会注意到"这个文件和上次记录的不一样了"，但它只是把这个文件列在 Changes 里，等着我决定要不要记录。

**Save 是文件层面的操作。**

### Commit（提交）

> Commit = 我认为这一组修改已经构成了一个值得记录的阶段，把它写进项目历史。

例子：我把 Kaggle Python 课程里 loops 那一节的笔记补完了，检查了一遍，觉得这一小块工作做完了。这时候我做一次 commit，Summary 写 `Add Python loops learning notes`。

**Commit 是项目历史层面的操作。**

这两者的差别我现在这样理解：

- 我可能按了 20 次 `Ctrl + S`，但只做 1 次 commit；
- Save 回答的是"我的文件现在是什么样"；
- Commit 回答的是"我的项目走到了哪一步"。

**保存是给电脑看的，提交是给人看的**——给未来的我，给任何打开这个仓库的人。

### Push（推送）

> Push = 把我本地已经记录好的历史，同步到 GitHub 的服务器上。

在 push 之前，我做的所有 commit 都只存在于我自己的电脑里。GitHub 上什么都看不到。

这一点我以前完全不知道。我以为 commit 就等于上传，所以有一次我 commit 完之后关了电脑，第二天在网页上找不到内容，还以为是 GitHub 出了问题。

### 四者的关系

```
  编辑器里改文字
        │
        │  Edit
        ▼
   Ctrl + S 保存
        │
        │  Save  ──────► 文件变了，但历史里还没有这一步
        ▼
  工作目录 Working Directory
        │
        │  Commit ─────► 写下"我做了什么、为什么"
        ▼                （此时只在我自己电脑上）
  本地历史 Local Repository
        │
        │  Push ───────► 同步到云端
        ▼
   GitHub（别人能看到了）
```

我现在记这个流程的方式是四个动词：

> **Edit → Save → Commit → Push**

前两个是我和文件之间的事，后两个是我和项目历史之间的事。

---

## 5. Why My Early Commit Messages Were Weak

现在回头看我那些 `update`、`day 3`、`modify`，问题其实很清楚。

### 它们没有携带任何信息

`update` 这个词的信息量是零。因为**任何一次 commit 都是一次 update**——如果没有更新，我根本不会提交。所以写 `update` 等于什么都没写。

`day 3` 稍微好一点，至少有时间线索。但它只回答了"什么时候"，而这个信息 Git 本来就自动记录了。它没有回答任何 Git 无法自动知道的事。

### 它们让 history 变成了一堵墙

我打开 commit history，期待看到的是一条学习路径。实际看到的是二十行几乎一样的字。

这时候要找"我是在哪一次修正了那个 DataFrame 索引的错误"，唯一的办法是一个一个点开看代码差异。**这比我不用 Git、直接翻文件还慢。**

### 根本原因：我把 commit message 当成了"必填框"

GitHub Desktop 的 Summary 框是必填的，不填就不能提交。所以我的心态是"这里必须写点什么，不然按钮是灰的"。

我在应付一个表单，而不是在做记录。

### 什么时候应该做一次 commit

我给自己定的规则只有一句：

> **一个 commit = 一个可以用一句话解释清楚的小任务。**

如果我要用"而且……还有……另外……"才能描述这次提交，那说明它应该被拆成两次或三次。

**好的 commit（示例）：**

- 完成 Pandas Lesson 3 的学习笔记
- 修正 DataFrame indexing 示例里的错误
- 补充 Python loops 的学习反思
- 添加 Kaggle Pandas 课程总结

每一条都是一件事，一句话说得完。

**不好的 commit：**

- 同时改了 README、Python 笔记、文件结构，还顺手删了两个旧文件
- 三天没提交，一次把所有东西攒在一起

### 为什么"小而完整"更好

我想到三个理由：

**第一，能写出好的 message。**这是最直接的。如果一次 commit 只做了一件事，Summary 自然就是那件事。写不出好 Summary，往往不是因为不会写，而是因为**这次提交本身就不是一件事**。

**第二，能被单独找到。**如果"修正索引错误"和"补充新笔记"混在同一次提交里，我以后就没办法单独定位那个修正。历史的颗粒度，决定了我以后能查到多细的东西。

**第三，逼我停下来想一想。**每次提交前问自己"我这次到底做了什么"，本身就是一次小小的复盘。攒三天再提交，就没有这个机会了。

---

## 6. How I Should Write Commit Messages

### Summary 的公式

我给自己定的规则：

> **动词 + 修改对象 + 核心变化**

英文示例：

```
Add Pandas filtering notes
Update Python loops reflection
Fix DataFrame indexing example
Add Kaggle Pandas course summary
Reorganize learning notes by course
Remove duplicated Python notes file
```

几条具体的写法约定：

- 用**祈使句现在时**：`Add` 而不是 `Added`；
- 开头动词大写，其余小写；
- 尽量控制在 50 个字符以内（超过会在 GitHub 上被截断）；
- 说"做了什么"，不说"改了哪个文件"（Git 已经知道改了哪个文件了）。

常用动词其实就那么几个：`Add`（新增）、`Update`（修改已有内容）、`Fix`（修正错误）、`Remove`（删除）、`Reorganize`（调整结构）、`Rename`（重命名）。

### Summary vs Description

这是我之前最没搞明白的地方。现在我这样区分：

| | 回答的问题 | 例子 |
|---|---|---|
| **Summary** | **What changed?** 这次主要做了什么 | `Add Pandas filtering notes` |
| **Description** | **Why? / What exactly?** 为什么改、具体改了什么、当时在想什么 | `Added examples for boolean indexing and clarified the difference between loc and iloc after redoing the Kaggle exercises. I had been using them interchangeably.` |

**Description 不是每次都要写。**

不需要写的情况——修改很小、意图一目了然：

```
Fix typo in README
Rename kaggle_python folder to kaggle-python
```

这些 Summary 已经说完了全部，再写 Description 就是重复。

建议写 Description 的情况：

- 这次改动比较多，Summary 一句话装不下；
- 修改的**原因**不明显（比如为什么突然删掉某个小节）；
- 涉及学习反思——我在这一步理解了什么、之前错在哪；
- 涉及数据处理——我为什么这样清洗、为什么排除某一年；
- 涉及研究方法或研究问题的变化；
- 我预感"以后可能会想不起来为什么这么做"。

最后这一条是我的核心判断标准。**如果我怀疑三个月后的自己会问"我当时为什么这样做"，那就现在写下来。**

---

## 7. Examples from My Kaggle Learning

> ⚠️ 说明：以下 commit 都是**示例**，用来演示改进前后的差别，不是我真实 commit history 的截图或复制。我真实的历史里大部分只有 `update`、`add notes`、`day 3` 这一类。

假设仓库结构是这样：

```text
learning-portfolio/
├── kaggle-intro-to-programming/
├── kaggle-python/
├── kaggle-pandas/
└── research-logs/
```

---

**示例 1 — 新建学习笔记**

修改内容：完成 Kaggle Pandas 第三课，新建了一份 groupby 的笔记。

- ❌ Summary：`update`
- ✅ Summary：`Add Pandas groupby learning notes`
- ✅ Description：`Notes from Kaggle Pandas Lesson 3, with examples from the exercises. Recorded where I got confused about the difference between groupby().count() and groupby().size().`

---

**示例 2 — 修改已有笔记**

修改内容：重看了 loops 那一节，把之前写得含糊的部分改清楚了。

- ❌ Summary：`modify`
- ✅ Summary：`Update Python loops notes with clearer examples`
- ✅ Description：`My earlier explanation of range() was vague and slightly wrong about the stop value. Rewrote it with a worked example.`

---

**示例 3 — 修正代码错误**

修改内容：发现笔记里一个 DataFrame 索引的例子跑不通。

- ❌ Summary：`fix`
- ✅ Summary：`Fix DataFrame indexing example in Pandas notes`
- ✅ Description：`The example used df['col'][0] to select a row, which happened to work only because the index was default integers. Replaced it with .loc and .iloc and explained why.`

> 这一条对我特别有意义。以前我改完就完事了，现在我会记下"错在哪、为什么会错"。**Description 在这里保存的不是修改，是理解。**

---

**示例 4 — 增加学习反思**

修改内容：学完 Kaggle Python 后，写了一段自己的总结。

- ❌ Summary：`add notes`
- ✅ Summary：`Add personal reflection after finishing Kaggle Python`
- ✅ Description：`What I found easy, what I still don't feel confident about (mainly functions and scope), and what I plan to review before starting pandas.`

---

**示例 5 — 调整文件结构**

修改内容：把散在根目录的笔记按课程分进三个文件夹。

- ❌ Summary：`change`
- ✅ Summary：`Reorganize notes into folders by Kaggle course`
- ✅ Description：`Root directory had 14 loose files and was getting hard to navigate. Grouped by course. No file contents changed, only locations.`

> "内容没变，只是移动了位置"这句话很重要。以后我看到这次提交动了 14 个文件，会以为发生了大事——这句话能让我一秒钟放心。

---

**示例 6 — 更新 README**

修改内容：在 README 里补上了每个文件夹的说明。

- ❌ Summary：`readme`
- ✅ Summary：`Update README with folder descriptions`

（这次不需要 Description，Summary 已经说完了。）

---

**示例 7 — 添加 research log**

修改内容：开始记录每天的学习日志。

- ❌ Summary：`day 1`
- ✅ Summary：`Add first entry to research log`
- ✅ Description：`Starting a dated log of what I work on each day, what I get stuck on, and what I decide. Previously this only existed in my head.`

---

**示例 8 — 删除重复文件**

修改内容：发现同一份笔记存了两个版本。

- ❌ Summary：`delete`
- ✅ Summary：`Remove duplicated Pandas notes file`
- ✅ Description：`pandas_notes_new.md was an earlier draft of pandas_notes.md. Checked that nothing in the draft was missing from the current file before deleting.`

> 删除类的提交我认为**一定要写 Description**。删掉的东西在文件列表里看不见了，只有 commit message 能说明它去哪了、我为什么确定可以删。

---

**示例 9 — 修正笔记里的理解错误**

修改内容：之前把 `is` 和 `==` 的区别写反了。

- ❌ Summary：`update python notes`
- ✅ Summary：`Correct explanation of is vs == in Python notes`
- ✅ Description：`I had written that is compares values. It compares identity. Found this while redoing an exercise.`

---

**示例 10 — 一个应该被拆开的 commit**

修改内容：某天晚上我同时改了 README、补了 pandas 笔记、删了一个旧文件、还调整了文件夹。

- ❌ Summary：`update everything`
- ✅ **正确做法不是改 message，而是拆成四次提交：**

```
Add Pandas merge notes
Remove outdated python_draft.md
Reorganize kaggle-pandas folder
Update README with new folder structure
```

> 这条是我最需要记住的。**有些 commit message 写不好，不是措辞问题，是这次提交本身包了太多东西。**

---

## 8. Should I Rewrite My Old Commits?

我确实想过这个问题：既然知道自己以前写得不好，要不要回头把那些 `update` 全部改掉？

技术上是可以的。Git 提供了修改历史的方法。但我决定**不改**。

理由有几个，从实际的到我更看重的：

**技术上的理由。**改写已经推送到 GitHub 的历史，会把所有旧 commit 的编号全部换掉。这在只有我一个人的仓库里不会造成协作问题，但它意味着我要用一堆自己还没真正搞懂的命令，去改一段本来运行得好好的历史。对我现在的水平来说，风险大于收益。

**记录上的理由。**如果我把当时的 message 改成现在的水平，那段历史就变成了一段"我从第一天起就懂 Git"的假记录。可我当时确实不懂。修改历史的操作只会改掉 message，改不掉我当时的实际理解——**它只是让记录和事实对不上了。**

**我最看重的理由。**那些糟糕的 commit message，本身就是我学习过程的一部分。

我现在的想法是：一个从 `update`、`day 3` 开始，中间某一天突然变成 `Fix DataFrame indexing example in Pandas notes`，然后一直保持下去的 commit history，**比一个从第一次提交就完美规范的历史更真实**。

因为后者只有两种可能：要么这个人一开始就受过训练，要么这段历史被修饰过。而前者展示的是一件更值得展示的事——**这个人在中途意识到了问题，并且改了。**

所以我选择的做法是：

1. **保留全部旧 commit history**，一条不动；
2. **在这份 `git_learning_notes.md` 里主动说明**：当时我对 Git 的理解不足，commit message 写得很随意，后来意识到了问题；
3. **从现在开始按规范写**；
4. **让后面的 commit history 自己去体现这个转变**，不需要我额外解释。

对一个学习型的 GitHub 来说，我觉得"从混乱到规范"是一条比"一开始就完美"更可信、也更有内容的线索。**我要展示的不是我一直很规范，而是我具备发现问题并改进的能力。**

---

## 9. My Commit Workflow from Now On

我给自己定的流程，尽量简单到不会因为麻烦而放弃：

### Step 1 — Edit：完成一个明确的小任务

不是"今天学习"，而是"补完 groupby 这一节的笔记"这种粒度。任务做完了再往下走。

### Step 2 — Review：在 GitHub Desktop 里看 Changes

这一步是我以前完全跳过的。现在我会认真看一遍左边的文件列表，问自己三个问题：

- 我到底改了什么？（点开看右边的差异，绿色是新增，红色是删除）
- 有没有误改的文件？（有时候会有莫名其妙的临时文件混进来）
- 这些修改是不是属于同一件事？（如果不是，先只勾选属于第一件事的文件，分两次提交）

### Step 3 — Explain：写 Summary

用一句话回答：**What did I change?**

动词 + 对象 + 核心变化。写不出来的话，回到 Step 2 —— 大概率是这次改动包含了不止一件事。

### Step 4 — 判断要不要写 Description

一个问题：**三个月后的我，会不会想知道"为什么"？**

会 → 写。不会 → 跳过。

### Step 5 — Commit

点 `Commit to main`。这时候修改被写进了本地历史。

### Step 6 — Push

点 `Push origin`。这时候 GitHub 上才能看到。

### 压缩成一句话

> **Edit → Review → Explain → Commit → Push**

这五个词我打算一直记着。以前我的流程只有 Edit → Commit → Push，缺的是中间那个 **Review** 和 **Explain**——而那两步恰好是把"上传文件"变成"记录过程"的关键。

---

## 10. My Personal Commit Rules

**1. One commit, one purpose.**
一次提交只做一件事。如果要用"而且"才能描述完，就该拆开。

**2. Never use `update` alone.**
`update`、`modify`、`change`、`new`、`day 4` 这类词单独出现时信息量为零，不再使用。

**3. Summary answers "what changed".**
动词 + 对象 + 核心变化，一句话说清这次做了什么。

**4. Description answers "why", when it matters.**
不是每次都写。判断标准：三个月后的我会不会问"为什么"。

**5. Review the Changes before committing.**
提交前一定看一遍改动列表，确认没有误改、没有混进无关文件。

**6. Do not mix unrelated files.**
README、笔记、文件结构调整、数据处理，属于不同的事，分开提交。

**7. Commit when a small step is complete — not by the clock.**
按"完成了一个小任务"提交，而不是按"今天结束了"提交。

**8. Deletions always need a reason.**
删除类的提交必须写 Description，说明删掉的是什么、为什么可以删。

---

## 11. From Learning Notes to Research Projects

我现在正准备开始一个数据分析研究项目。想清楚 commit 这件事，很大程度上是因为我意识到：**在研究项目里，写不好 commit 的代价会比在学习笔记里大得多。**

学习笔记的 commit history 乱一点，最坏的结果是我找不到某篇笔记的修改记录。但研究项目不一样。

一个研究项目做上几个月，可能会产生这样一串提交（**以下为示例**）：

```
Import raw tourism data from statistical yearbook
Record data source details in data_sources.md
Clean tourism dataset and align years
Fix missing-value handling for 2020-2022
Add descriptive statistics notebook
Create tourism trend figure
Revise research question after checking data coverage
Update methodology notes on index base year
```

如果这条历史记录得好，它能回答一些**只靠看最终文件永远回答不了的问题**：

- **数据是什么时候加进来的？**从哪个来源？——第一、二条提交回答了。
- **清洗规则什么时候变过？**——第四条。而且如果我在 Description 里写了原因，我还能知道为什么变。
- **某张图是什么时候、基于哪一版数据生成的？**——第六条的时间点决定了它用的是第四条修正之前还是之后的数据。这直接关系到那张图对不对。
- **研究问题为什么变了？**——第七条。这可能是整个项目里最重要的一次提交。研究方向的调整如果不记录，事后就只剩下"我一开始就是这么想的"这种不真实的叙述。
- **某个错误是从哪一步开始的？**——如果我发现某个数字不对，我可以沿着历史往回找，定位到是哪一次修改引入的。
- **结论是怎么一步步形成的？**——整条链本身就是答案。

还有一层我觉得更重要。

在数据研究里，**"为什么"往往比"是什么"更关键**。为什么排除某一年的数据？为什么换了一个指标？为什么放弃了原来的分析方法？这些判断如果没有当场记录下来，几个月后连我自己都会想不起来，最后只能凭印象重新编一个理由——而那个理由未必是当时真实的想法。

commit message 恰好是一个天然的记录点：**它必须在我做这个决定的那一刻写下来，而且带着无法伪造的时间戳。**

所以我现在的认识是：

> Git 不只是一个代码管理工具，它也可以是一个研究过程的记录工具。

对我这种不打算做软件工程师、但要长期做数据分析的人来说，后面这个用途可能比前面那个更有价值。

---

## 12. Reflection

> At first, I thought GitHub was mainly a place to store finished files.
> Now I understand that its real value is also in preserving how a project develops over time.

这句话是我写这篇笔记最想留下的东西。

我最初用 GitHub，目的很单纯：让我的学习笔记有个地方放，最好还能让别人看到。那时候我心里的"成果"，就是仓库里那几个文件。至于这些文件是怎么来的、中间改过几次、我在哪里卡住过、哪一段是我第二次才写对的——这些我不觉得重要，也不觉得需要保存。

现在我的想法变了。

我意识到我学 Git 并不是为了成为软件工程师。我以后要做的是 Python、数据分析和经济学研究。在这些事情里，我真正需要的是：

**保留清晰的工作过程。**不只是最后那个跑得通的 notebook，还有中间那些跑不通的版本、那些被我推翻的想法。

**知道自己每一步做了什么。**一个项目做三个月，人的记忆是靠不住的。我需要一个比记忆可靠的东西。

**让研究具有可追溯性。**每一张图能追到数据，每一次清洗能追到理由，每一个结论能追到它形成的那一步。这不是形式要求——这是判断一个结论能不能站得住的前提。

**让未来的自己能够重新理解今天的决定。**我现在越来越确信，研究里最容易丢失的不是数据，是当时的判断依据。数据文件会一直躺在那里，但"我为什么这样处理它"如果不写下来，几周就没了。

**让别人看到的不只是结果，也能看到过程。**

写到这里我发现，这几条其实指向同一件事。

我以前理解的 GitHub 是一个**存放地**——东西做完了，放进去。现在我理解的 GitHub 是一条**路径**——它记录的不是终点，是我怎么走到终点的。

而 commit，就是这条路径上的一个个脚印。以前我随手写的那些 `update`，等于是走过之后没有留下脚印，只留下了"我到过这里"的模糊印象。

所以最后我想把这个认识写成一句话，提醒以后的自己：

> **一个好的 GitHub 项目，不只是展示"我做出了什么"，也应该能够展示"我是怎样一步一步做到的"。**

我现在还远远谈不上把 Git 用好了。我会的只是 GitHub Desktop 上的几个按钮，命令行几乎没碰过，分支、合并这些概念也还没真正理解。但至少从今天开始，我知道自己每次点 Commit 之前，应该先停下来问一句：

> 我这次到底做了什么？未来的我会想知道什么？

这个问题看起来很小，但它是我从"上传文件"走向"记录过程"的第一步。
