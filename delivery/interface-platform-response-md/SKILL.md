---
name: interface-platform-response-md
description: Generate Markdown for the Huayi interface management platform, covering interface basic info, request parameters, response parameters, status codes, and examples with `/Pecms` request paths, JSON request examples, and nested field tables.
---

# Interface Platform Response Markdown

## 适用场景

- 用户要求为接口管理平台整理接口文档。
- 当前主要整理接口管理平台录入所需的核心字段区块，而不是完整接口手册。
- 输出格式为 Markdown 表格，后续由用户复制到接口管理平台。

## 默认规则

1. 默认整理的章节顺序为：
   - `接口基本信息`
   - `请求参数`
   - `响应参数`
   - `响应状态`
   - `响应示例`
   - `说明`
2. 请求地址优先使用用户给出的地址。
   - 如果用户未单独指定，华谊开放接口默认写为 `/Pecms/open/api/...`。
3. 请求参数按接口管理平台录入口径整理。
   - 如果接口有请求头参数，先列“请求头参数”表。
   - 如果平台界面按 JSON 内容区录入请求参数，则补“请求参数示例（JSON格式）”。
   - JSON 示例后再补“参数说明”表。
   - 对 `multipart/form-data`、`application/json` 等真实请求类型，需要在“接口基本信息”中明确写出。
4. 响应参数统一采用三列表格：
   - `字段名 | 字段名说明 | 字段类型`
5. 接口返回数组时：
   - 直接列“单个数组对象字段”。
   - 不额外写“data 数组对象字段”这类平台包裹描述，除非用户要求。
6. 接口返回分页对象时：
   - 先列分页字段，如 `totalCount`、`pageSize`、`totalPage`、`currPage`、`list`。
   - 再单独列 `list` 数组对象字段。
7. 接口返回嵌套对象或数组时：
   - 顶层表格先列对象/数组字段。
   - 再为对应字段补充子表格，例如 `files 数组对象字段`、`jobList 数组对象字段`。
8. 动态结构字段要如实表述。
   - 例如 `reportData`、`reports`、`regionB`、`regionC`，类型可写为 `Array<Object>` 或 `Array<Map>`。
9. 默认补充响应状态。
   - 至少列出接口管理平台需要录入的状态码与说明。
   - 如用户已给出截图或标准口径，优先按用户提供的状态码整理。
10. 默认补充响应示例。
   - 响应示例应与实际返回结构一致，可保留 `msg`、`code`、`data` 的完整 JSON。
11. 默认不单列公共响应结构表。
   - `msg`、`code`、`data` 可保留在“响应示例”中。
   - 只有用户明确要求时，才补充公共响应结构表。
12. 说明文字只保留必要业务说明。
   - 不写源码路径、提交记录、内部测试口径。

## 推荐结构

```md
# <接口名称>-响应参数

## 接口基本信息

- 接口名称：...
- 请求方式：`GET/POST`
- 请求地址：`/Pecms/open/api/...`
- 请求类型：`application/json/multipart/form-data`

## 请求参数

### 请求头参数

| 字段名 | 字段名说明 | 是否必填 | 字段类型 |
| --- | --- | --- | --- |
| ... | ... | 是/否 | ... |

### 请求参数示例（JSON格式）

```json
{
  "id": "123"
}
```

### 参数说明

| 字段名 | 字段名说明 | 是否必填 | 字段类型 |
| --- | --- | --- | --- |
| ... | ... | 是/否 | ... |

## 响应参数

| 字段名 | 字段名说明 | 字段类型 |
| --- | --- | --- |
| ... | ... | ... |

## <嵌套字段> 对象字段

| 字段名 | 字段名说明 | 字段类型 |
| --- | --- | --- |
| ... | ... | ... |

## 响应状态

| 状态码 | 说明 |
| --- | --- |
| 00000 | ok |

## 响应示例

```json
{
  "msg": "SUCCESS",
  "code": "00000",
  "data": {}
}
```

## 说明

- ...
```

## 华谊项目专用约束

1. 字段名以实际响应 DTO 为准。
2. 字段说明优先采用 Swagger 注释、代码注释和业务命名。
3. 纯 Web 页面不纳入接口管理平台材料。
4. 当接口已由新接口替代时，只整理最新有效接口。
5. 如果用户先确认单个接口格式，再批量整理其余接口，后续输出必须沿用已确认格式。
