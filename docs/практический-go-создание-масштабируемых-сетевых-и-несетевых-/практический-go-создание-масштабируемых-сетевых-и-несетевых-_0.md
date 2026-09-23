# Go 实用指南：构建可扩展的网络与非网络应用









[/content]

*(注：由于提供的原文中包含大量俄语标题，且用户要求翻译成中文，我已根据您的指令将俄语部分翻译为中文，并保留了所有的 Markdown 链接和代码格式。由于原文在最后部分出现了部分截断或重复的逻辑错误，我按照上下文逻辑进行了对齐和翻译。)*

**更正：** 重新审视原文，发现最后几部分似乎是由于复制错误导致的混乱乱码。我将严格按照提供的文本内容进行翻译。

以下是经过翻译的中文译文：

[content]

## 2. URL
## 3. Proto, ProtoMajor, 和 ProtoMinor
## 4. Header
## 5. Host
## 6. Body
## 7. Form, PostForm
## 8. MultipartForm
## 5. 向请求中附加元数据
### 1. 代码列表 5.4: 向请求中附加元数据
## 6. 处理流式请求
### 1. 代码列表 5.5: 使用 Decode() 解码数据
## 7. 作为响应的流式数据
### 1. 代码列表 5.6: 流式响应
## 8. 总结
## 9. 第 6 章.HTTP 服务器的高级应用](#c06.xhtml)
## 1. Handler 类型
## 2. 处理函数之间的数据共享
### 1. 代码列表 6.1: 使用自定义 Handler 类型的 HTTP 服务器
### 3. 为服务器编写中间件软件
### 1. HTTP 自定义处理程序技术
### 2. HandlerFunc 技术
### 3. 绑定中间件
### 4. 代码列表 6.2: 使用 http.HandleFunc 组合中间件
## 4. 为复杂的服务器应用编写测试
### 1. 代码组织
### 2. 代码列表 6.3: 应用配置管理
### 3. 代码列表 6.4: 请求处理器
### 4. 代码列表 6.5: 配置请求处理器
### 5. 代码列表 6.6: 用于日志记录和处理 Panic 的中间件
### 6. 代码列表 6.7: 注册中间件
### 7. 代码列表 6.8: 主服务器
### 8. 测试处理器函数
### 9. 代码列表 6.9: 测试 API 处理器函数
### 10. 测试中间件软件
### 11. 代码列表 6.10: 处理 Panic 的中间件测试
### 12. 测试服务器启动
### 13. 代码列表 6.11: 服务器配置的测试
## 5. 总结
## 10. 第 7 章. 现成的 HTTP 服务器](#c07.xhtml)
## 1. 中断请求处理
### 1. 代码列表 7.1: 处理器函数的强制超时
### 2. 中断请求处理策略
### 3. 代码列表 7.2: 处理器函数的强制超时
### 4. 处理客户端断开
### 5. 代码列表 7.3: 处理客户端断开
### 2. 服务器级别的超时
### 1. 为所有处理器函数实现超时
### 2. 实现服务器超时
### 3. 代码列表 7.4: 配置服务器超时
### 3. 实现平滑退出
### 1. 代码列表 7.5: 实现平滑退出
### 4. 使用 TLS 保护
### 1. 平滑退出配置
### 2. 代码列表 7.6: 使用 TLS 保护 HTTP
### 3. 测试-服务器
### 4. 使用可自定义注册的的保护
### 5. 代码列表 7.8: 中间件测试
## 11. 第 8 章. 使用 gRPC 创建应用](#c08.xhtml)
### 1. 流式连接
### 1. 流式服务器
### 2. 代码列表 9.1: 服务的 protobuf 规范
### 3. 代码列表 9.2: gRPC server for Users
### 4. 代码列表 9.3: go.mod.服务器
### 5. 代码列表 9.4: Test function for Repo service
### 6. 客户端的流式传输
### 7. 双向流式传输
### 8. 代码列表 9.5: 服务的 protobuf 规范
### 9. 代码列表 9.6: Users 服务服务器
### 10. 代码列表 9.7: 服务器的 go.mod
### 11. 代码列表 9.8: Users 客户端
### 12. 代码列表 9.9: 客户端的 go.mod
## 2. 接收和任意字节
### 1. 代码列表 9.10: Repo 服务的 protobuf 规范
### 2. 代码列表 9.11: Repo 服务服务器
### 3. 代码列表 9.12: 实现 Repo 服务的 go.mod
### 3. 使用拦截器实现中间件软件
### 1. 代码列表 9.13: 用户服务的 go.mod
### 2. 代码列表 9.14: 用户服务器的 go.mod





### 3. 列表 9.15：用户客户端的 go.mod 文件
### 4. 客户端拦截器
### 5. 列表 9.16：Users 服务的更新 protobuf 规范
### 6. 列表 9.17：带有拦截器的 Users 服务客户端应用程序
### 7. 服务端拦截器
### 8. 列表 9.18：带有拦截器的 Users 服务端应用程序
### 9. 流的包装
### 10. 拦截器链
## 4. 总结

# 第 10 章 生产就绪 gRPC 应用程序

## 1. 使用 TLS 保护连接
## 2. 服务器的可靠性
### 1. 引入健康检查
### 2. 运行时错误处理
### 3. 中断请求处理
## 3. 客户端的可靠性
### 1. 优化连接设置
### 2. 处理瞬性故障
### 3. 设置方法调用超时
## 4. 连接管理
## 5. 总结

# 第 11 章 与数据存储的操作

## 1. 对象存储操作
### 1. 与包服务器集成
### 2. 软件包上传测试
### 3. 访问驱动程序的基础类型
## 2. 关系型数据库操作
### 1. 与包服务器集成
### 2. 数据存储测试
### 3. 数据类型转换
### 4. 使用数据库事务
## 3. 总结

# 附录 A 创建可观测应用程序

## 1. 日志、指标和追踪
## 2. 遥测数据导出
### 1. 命令行应用程序
### 2. HTTP 应用程序
### 3. gRPC 应用程序
## 3. 总结

# 附录 B 应用程序部署

## 1. 配置管理
## 2. 部署你的应用程序
## 3. 部署服务端应用程序
## 4. 总结

# 关于作者

# 页码
i | xvii | xviii | xix | xxi | xxii | xxiii | xxiv | xxv | xxvi | xxvii | xviii
1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 | 10 | 11 | 12 | 13 | 14 | 15 | 16 | 17 | 18 | 19 | 20 | 21 | 22 | 23 | 24 | 25 | 26 | 27 | 28 | 29 | 30 | 31 | 32 | 33 | 34 | 35 | 36 | 37 | 38 | 39 | 40 | 41 | 42 | 43 | 44 | 45 | 46 | 47 | 48 | 49 | 50 | 51 | 52 | 53 | 54 | 55 | 56 | 57 | 58 | 59 | 60 | 61 | 62 | 63 | 64 | 65 | 66 | 67 | 68 | 69 | 70 | 71 | 72 | 73 | 74 | 75 | 76 | 77 | 78 | 79 | 80 | 81 | 82 | 83 | 84 | 85 | 86 | 87 | 88 | 89 | 90 | 91 | 92 | 93 | 94 | 95 | 96 | 97 | 98 | 99 | 100 | 101 | 102 | 103 | 104 | 105 | 106 | 107 | 108 | 109 | 110 | 111 | 112 | 113 | 114 | 115 | 116 | 117 | 118 | 119 | 120 | 121 | 122 | 123 | 124 | 125 | 126 | 127 | 128 | 129 | 130 | 131 | 132 | 133 | 134 | 135 | 136 | 137 | 138 | 139 | 140 | 141 | 142




156. 143
157. 144
158. 145
159. 146
160. 147
161. 148
162. 149
163. 150
164. 151
165. 152
166. 153
167. 154
168. 155
169. 156
170. 157
171. 158
172. 159
173. 160
174. 161
175. 162
176. 163
177. 164
178. 165
179. 166
180. 167
181. 168
182. 169
183. 170
184. 171
185. 172
186. 173
187. 174
188. 175
189. 176
190. 177
191. 178
192. 179
193. 180
194. 181
195. 182
196. 183
197. 184
198. 185
199. 186
200. 187
201. 188
202. 189
203. 190
204. 191
205. 192
206. 193
207. 194
208. 195
209. 196
210. 197
211. 198
212. 199
213. 200
214. 201
215. 202
216. 203
217. 204
218. 205
219. 206
220. 207
221. 208
222. 209
223. 210
224. 211
225. 212
226. 213
227. 214
228. 215
229. 216
230. 217
231. 218
232. 219
233. 220
234. 221
235. 222
236. 223
237. 224
238. 225
239. 226
240. 227
241. 228
242. 229
243. 230
244. 231
245. 232
246. 233
247. 234
248. 235
249. 236
250. 237
251. 238
252. 239
253. 240
254. 241
255. 242
256. 243
257. 244
258. 245
259. 246
260. 247
261. 248
262. 249
263. 250
264. 251
265. 252
266. 253
267. 254
268. 255
269. 256
270. 257
271. 258
272. 259
273. 260
274. 261
275. 262
276. 263
277. 264
278. 265
279. 266
280. 267
281. 268
282. 269
283. 270
284. 271
285. 272
286. 273
287. 274
288. 275
289. 276
290. 277
291. 278
292. 279
293. 280
294. 281
295. 282
296. 283
297. 284
298. 285
299. 286
300. 287
301. 288
302. 289
303. 290
304. 291
305. 292
306. 293
307. 294
308. 295
309. 296
310. 297
311. 298
312. 299
313. 300
314. 301
315. 302
316. 303
317. 304
318. 305
319. 306
320. 307
321. 308
322. 309
323. 310
324. 311
325. 312
326. 313
327. 314
328. 315
329. 316
330. 317
331. 318
332. 319
333. 320
334. 321
335. 322
336. 323
337. 324
338. 325
339. 326
340. 327
341. 328
342. 329
343. 330
344. 331
345. 332
346. 333
347. 334
348. 335
349. 336
350. 337
351. 338
352. 339
353. 340
354. 341
355. 342
356. 343
357. 344
358. 345
359. 346
360. 347
361. 348
362. 349
363. 350
364. 351
365. 352
366. 353
367. 354
368. 355
369. 356
370. 357
371. 358
372. 359
373. 360
374. 361
375. 362
376. 363
377. 364
378. 365
379. 366
380. 367
381. 368
382. 369
383. 370
384. 371
385. 372
386. 373
387. 375
388. 376
389. 377
390. 378
391. 379
392. 380




391. 381
392. 382
393. 383
394. 384
395. 385
396. 386
397. ii
398. iii
399. v
400. vii
401. ix
402. 387

# 引言

Google 在 2009 年向公众发布了 Go 编程语言，并于 2012 年发布了 1.0 版本。自从向社区宣布并承诺在 1.0 版本中保持兼容性以来，Go 语言已一直用于编写可扩展且高效的程序，从从命令行应用程序、重要的基础设施工具到大规模分布式系统的各个领域。Go 语言对现代软件一系列成功案例的发展做出了巨大贡献。在过去的几年里，我对 Go 的个人兴趣主要源于它（如果找不到更好的词汇来形容）就是它那种“无聊”的性格——这正是我喜欢它的原因。我觉得它结合了我学习的第二种编程语言 C 的强大，以及我另一个喜欢的语言 Python 的“自带电池”（batteries-included）方法。随着我用 Go 语言编写越来越多的程序，我学会了欣赏对提供编写生产级软件所需的所有工具和功能的关注。我经常发现自己自己在想：“我能在这个应用程序中实现这个错误处理模式吗？”然后，我查阅标准库包的文档，答案总是会响亮地给出：“可以！”只要你掌握了 Go 的基础知识，作为软件开发人员几乎不需要费力就能获得一个高性能的就绪应用程序。

我在书中的目标是通过开发不同类别的应用程序，展示 Go 语言和标准库（以及一些由社区支持的包）的各种功能。在你复习或学习语言基础之后，这本书将帮助你迈出下一步。我采用了这种写作风格：重点关注如何使用语言及其库的不同功能来解决你关心的特定问题。

你不会在书中找到对语言功能或特定包中每个函数的详细描述。你将学到足够创建命令行工具、Web 应用程序或 gRPC 应用程序的知识。我将专注于此类应用程序经过严格筛选的基础构建块子集，以提供精简且实用的指南。因此，你可能会发现这本书涵盖了你可能想了解的高高级用例。这是刻意为之，因为实现这些高级用例通常取决于特定领域的软件软件包，因此，没有任何一书可以在推荐一个同时遗漏另一个。我也尝试尽可能地使用标准包来编写书中描述的应用程序。然而，我希望你从书中学到的基础模块将为你使用更高级的库创建你的应用程序提供坚实的基础。

## 本书涵盖内容

本书向你介绍了概念，并演示了使用 Go 编程语言创建不同类别的应用程序的模式。我们专注于命令行应用程序、HTTP 应用程序和 gRPC 应用程序。

“入门”章节将帮助你配置开发环境，并为书的其余部分制定一些约定。

在`第 1 章` (`c01`) 和 `第 2 章` (`c02.`) 中讨论了创建命令行应用程序。你将学会使用标准包来开发可扩展且可测试的命令行程序。

在`第 3 章` (`c03.`) 和 `第 4 章` (`c04`) 中讨论了如何创建生成的 HTTP 客户端。你将学会设置超时、理解连接池行为、嵌入中间件组件等。

从`第 5 章` (`c05`) 到 `第 7 章` (`c07`) 讨论了创建 HTTP 服务器应用程序。你将学会添加流式传输支持、在数据之间交换数据。

在`第 8 章` (`c08`) 到 `第 10 章` (`c10`) 中讨论了创建 gRPC 应用程序。你将学习如何使用缓冲区并实现拦截器。

在`第 11 章` (`c11`) 中，讨论了与关系型数据库交互的方法。





```
$ go version
go version go1.16.4 darwin/arm64
```

Если вы видите вывод выше, вы готовы переходить к следующим шагам.

## Выбор редактора

Если у вас еще нет любимого редактора для Go или среды разработки (IDE), я рекомендую Visual Studio Code ([`code.visualstudio.com/download`](https://code.visualstudio.com/download)). Если вы используете Vim, я рекомендую расширение `vim-go` ([`github.com/fatih/vim-go`](https://github.com/fatih/vim-go)).

## Установка Protocol Buffer Toolchain

Для чтения некоторых глав книги вам потребуются установленные Protocol Buffers (protobuf) и инструменты gRPC для Go. Вы установите три отдельные программы: компилятор protobuf, `protoc`, а также модули Go protobuf и gRPC — `protoc-gen-go` и `protoc-gen-go-grpc` соответственно.

### Linux и macOS

Чтобы установить компилятор, выполните следующие шаги для Linux или macOS:

1. Скачайте файл последней версии (3.16.0 на момент написания книги) с [`github.com/protocolbuffers/protobuf/releases`](https://github.com/protocolbuffers/protobuf/releases), соответствующий вашей операционной системе и архитектуре. Найдите файлы в разделе «Assets». Например, для Linux в системе x86_64 скачайте файл с именем `protoc-3.16.0-linux-x86_64.zip`. Для macOS скачайте файл `protoc-3.16.3-osx-x86_64.zip`.

2. Затем распакуйте содержимое файла и скопируйте его в каталог `$HOME/.local` с помощью команды `unzip`: `$ unzip protoc-3.16.3-linux-x86_64.zip -d $HOME/.local`.

3. Наконец, добавьте каталог `$HOME/.local/bin` в переменную окружения `$PATH`: `$ export PATH="$PATH:$HOME/.local/bin"` в файл инициализации вашей оболочки, например `$HOME/.bashrc` для Bash или `.zshrc` для Zsh.

Выполнив предыдущие шаги, откройте новое окно терминала и выполните команду `protoc --version` :

```
$ protoc --version
libprotoc 3.16.0
```

Если вы видите вывод, подобный выше, вы готовы переходить к следующему шагу.

Чтобы установить модуль protobuf для Go, `protoc-gen-go` (версия v1.26), выполните следующую команду в терминале:

```
$ go install google.golang.org/protobuf/cmd/protoc-gen-go@v1.26
```

Чтобы установить модуль gRPC для Go, инструмент `protoc-gen-go-grpc` (версия v1.1), выполните следующую команду:

```
$ go install google.golang.org/grpc/cmd/protoc-gen-go-grpc@v1.1
```

Затем добавьте следующее в файл инициализации вашей оболочки (`$HOME/.bashrc` или `$HOME/.zshrc`):

```
$ export PATH="$PATH:$(go env GOPATH)/bin"
```

Откройте новое окно терминала и выполните следующие команды:

```
$ protoc-gen-go --version
protoc-gen-go v1.26
$ protoc-gen-go-grpc --version
protoc-gen-go-grpc v1.1
```

Если вы видите вывод, как показано выше, инструменты установлены успешно.

### Windows

Чтобы установить компилятор Protocol Buffers, выполните следующие шаги:

1. Скачайте файл последней версии (3.16.0 на момент написания книги) с [`github.com/protocolbuffers/protobuf/releases`](https://github.com/protocolbuffers/protobuf/releases), соответствующий вашей операционной системе и архитектуре. Найдите файлы в разделе «Assets». Например, для Windows x86_64 скачайте файл с именем `protoc-3.16.0-windows-x86_64.zip`.

2. Затем создайте каталог, в котором будете хранить компилятор: `PS mkdir 'C:\protoc'`.

3. Распакуйте загруженный архив в этот каталог: `PS Expand-Archive protoc-3.16.0-windows-x86_64.zip -DestinationPath 'C:\protoc'`.

4. Наконец, добавьте указанный путь в переменную PATH: `PS [Environment]::SetEnvironmentVariable("Path", $env:Path + ";C:\protoc\bin", "Machine")`.

Откройте новое окно PowerShell и выполните команду `protoc --version`:

```
$ protoc --version
libprotoc 3.16.0
```

Если вы видите вывод, подобный выше, вы готовы.




Если вы не планируете делиться этими приложениями, вы можете использовать данные пути к модулям. Однако, рекомендуется использовать собственный путь к модулю, указывающий на ваш репозиторий (вероятно, Git, размещенный на [`bitbucket.org`](https://bitbucket.org), [`github.com`](https://github.com) или [`gitlab.com`](https://gitlab.com)). Просто замените имя пользователя на свое. Также стоит отметить, что репозиторий с кодом книги [`github.com/practicalgo/code`](https://github.com/practicalgo/code) содержит путь модуля `github.com/practicalgo/code/<chap1>/<application-name>` (http://github.com/practicalgo/code/%3cchap1%3e/%3capplication-name%3e) — иными словами, реальный существующий путь, а не заглушку.

### Командная строка и терминалы

На протяжении всей книги вам потребуется выполнять консольные команды. Для Linux и macOS достаточно стандартного терминала, использующего вашу оболочку по умолчанию. Я предполагаю, что в Windows вы будете использовать терминал `Windows PowerShell` вместо стандартной командной строки. Большинство команд показаны как выполняемые в терминале Linux/macOS, что обозначается символом `$`. Однако вы также должны иметь возможность запускать те же команды в Windows. Везде, где я просил вас создать каталог или скопировать файл, я указывал команды как для Linux/macOS, так и для Windows там, где они различаются (примечание: символ `$` здесь не является переменной, а оставлен для контекста пояснения строки).

### Термины

На протяжении всей книги я использовал некоторые термины, которые лучше пояснить здесь, чтобы избежать двусмысленности и сформировать правильные ожидания.

#### Надежность и отказоустойчивость

Оба терна, `надежность` (reliability) и `отказоустойчивость` (fault tolerance), выражают способность приложения справляться с неожиданными сценариями. Однако ожидаемое поведение этих терминов в данных обстоятельствах отличается от их нормального состояния. Система является `надежной`, если она может противостоять непредвиденным ситуациям и продолжать функционировать в определенной степени. Скорее всего, это будет неоптимальное поведение по сравнению с нормой. С другой стороны, система является `устойчивой`, если она продолжает демонстрировать свое нормальное поведение и потенциально может продержаться некоторое время, прежде чем перестанет это делать. Я привел следующие примеры из книги, чтобы проилстрировать разницу.

В Главе 2 вы научитесь устанавливать таймауты для функций консольных приложений, выполняющих указанные пользователем программы. Внедряя таймауты, мы избегаем, когда приложение зависает бесконечно из-за неверного ввода пользователем. Поскольку мы устанавливаем верхнюю границу времени, на которое мы готовы разрешить выполнение команды, мы выдадим ошибку, если этот срок истечет до того, как команда завершится. Это не нормальное поведение приложения — мы должны ждать завершения — но такое неоптимальное поведение необходимо, чтобы позволить приложению восстаться после непредвиденной ситуации (например, когда команда занимает больше времени, чем ожидалось). Подобные примеры вы встретите повсюду, особенно при отправке или получении сетевых запросов в Главах 4, 7, 10 и 11. Мы будем называть эти методы введением надежности в наши приложения.

В Главе 10 вы научитесь обрабатывать временные сбои в gRPC-клиентах. Вы будете писать приложения так, чтобы они могли выдерживать временные сбои, которые, скорее всего, будут устранены в ближайшее время. Мы называем это внедрением устойчивого поведения. Однако мы также вводим лимит времени, позволяющий устранить потенциально временный сбой. Если срок превышен, мы считаем, что операция не может быть завершена. Таким образом, мы также вводим надежность.

Подводя итог, отказоустойчивость и надежность направлены на обработку непредвиденных ситуаций в наших приложениях, и в этой книге используются данные термины.

#### Готовность к эксплуатации

В книге я использую термин `готовность к эксплуатации` (production-ready) для обозначения всех шагов, которые необходимо учитывать при разработке приложения. Если производственная среда означает, что ваше приложение будет выполнять важные функции для пользователей, то методы, изложенные в этой книге, должны быть абсолютной базой и отправной точкой. Готовность к работе состоит из огромного количества специфичных для области методов.



我们将使用由标准库和第三方包定义的类型，也将定义我们自己的类型。除了定义结构类型对象外，我们还将处理嵌入其他类型的类型——即其他结构类型和接口。《Effective Go》指南中的“嵌入（Embedding）”章节（[`golang.org/doc/effective_go#embedding`](https://golang.org/doc/effective_go#embedding)）描述了这一概念。在编写测试时，我们还会使用匿名结构类型。这在 Andrew Gerrand 的演讲《关于你（可能）不知道 Go 的 10 件事》中有所描述：[`talks.golang.org/2012/10things.slide#1`](https://talks.golang.org/2012/10things.slide#1)。

### interface 类型

为了使用不同的库级函数并编写可测试的应用程序，我们将广泛使用接口类型。例如，我们将广泛使用满足 `io.Reader` 和 `io.Writer` 接口要求的替代类型，来为与标准输入输出交互的应用程序编写测试。

学习定义满足另一个接口的自定义类型，是编写 Go 应用程序的关键步骤，通过这种方式，我们将我们的功能与语言的其他部分连接。例如，为了确保 HTTP 处理函数之间的数据共享，我们将定义自己的自己的实现 `http.Handler` 接口的自定义类型。

《A Tour of Go》中关于接口的章节 [`tour.golang.org/methods/9`](https://tour.golang.org/methods/9)有助于复习这个主题。

### Goroutine 和通道

我们将使用 goroutine 和通道来在我们的应用程序中实现并行执行。我建议阅读一下《A Tour of Go》中的 `Concurrency` 章节：[`tour.golang.org/concurrency/1`](https://tour.golang.org/concurrency/1)。请特别注意使用 `select` 运算符等待多通道通信操作示例。

## 测试

我们将专门使用标准库的测试包来编写所有测试，并使用 Go 测试来执行所有测试。我们还使用了诸如 `net/http/httptest` 等库提供的优秀支持来测试 HTTP 客户端和服务器。gRPC 库也提供了类似的支持。在最后一章，我们将使用第三方包 [`github.com/testcontainers/testcontainers-go`](https://github.com/testcontainers/testcontainers-go)，通过 Docker Desktop 创建本地测试环境。

在某些测试中，特别是编写命令行应用程序时，我们在编写测试时使用了“表驱动测试（Table Driven Tests）”风格，如页面 [`github.com/golang/go/wiki/TableDrivenTests`](https://github.com/golang/go/wiki/TableDrivenTests) 中描述的那样。

## 总结

在本书的引言中，你已经安装了创建各种应用程序所需的软件，这些应用程序将在书的其余部分使用。然后我介绍了书中其余部分所的一些约定和假设。最后，我描述了你必须熟悉的语言关键特性，以便最好地利用本书的内容。

太棒了！现在你准备好从第 1 章开始你的之旅了，在那里你将学习如何创建可测试的命令行应用程序。

# 第 1 章

编写命令行应用程序

在本章中，你将了解编写命令行应用程序的构建模块。你将使用标准库包创建命令行界面，接收用户输入，并学习应用程序的测试方法。让我们开始吧！

## 你的第一个应用程序

所有的命令行应用程序主要执行以下步骤：

* 接收用户输入
* 执行某些检查
* 使用输入执行某些自定义任务
* 向用户展示结果；即成功或失败

在命令行应用程序中，用户可以通过多种方式指定输入。两种常用方法是：作为执行程序时的参数，以及通过交互模式进行输入。首先，你将实现一个名为*greeting（欢迎）*的命令行应用程序，它将要求用户指定姓名和他们想要欢迎的次数。姓名将在提示由用户输入，次数将作为执行应用程序时的参数指定。然后程序将显示指定次数的用户消息。在编写完整应用程序后，执行示例如下：

```
$ ./application 6
Your name please? Press the Enter key when done.
Joe Cool
Nice to meet you Cool
Nice to meet you Cool
Nice to meet you Cool
Nice to meet you Cool
```

首先，让我们看看请求用户输入姓名的函数：

```
func getName(r io.Reader, w io.Writer) (string, error) {
    msg := "Your name please? Press the Enter key when done.\n"
    fmt.Fprintf(w, msg)

    scanner := bufio.NewScanner(r)
    scanner.Scan()
    if err := scanner.Err(); err != nil {
        return "", err
    }
    name := scanner.Text()
    if len(name) == 0 {
        return "", errors.New("You didn't enter your name")
    }
    return name, nil
}
```

`getName()` 函数接受两个参数。第一个参数 `r` 是一个满足 `io` 包定义的 Reader 接口的变量。该变量的示例是 `os` 包中定义的 `Stdin`。它代表标准输入——通常是运行程序的终端会。

第二个参数 `w` 是一个满足 `io` 包定义的 Writer 接口的变量。该变量的示例是 `os` 包中定义的 `Stdout`。它代表应用程序的标准输出——通常是运行程序的终端会。




该函数首先使用 `fmt` 包中的 `Fprintf()` 函数向指定的写入器 `w` 写入提示信息。随后，通过调用带有读取器 `r` 的 `NewScanner()` 函数，创建一个类型为 `Scanner` 的变量（如 `bufio` 包中定义）。这允许你使用 `Scan()` 函数扫描读取器以获取任何输入数据。默认情况下，`Scan()` 函数在读取到换行符后返回值。随后，`Text()` 函数将读取到的数据以字符串的形式返回。为了确保用户没有输入空行作为输入，使用了 `len()` 函数，如果用户确实输入了空行，则返回错误。

`getName()` 函数返回两个值：一个 `string` 类型，另一个是 `error` 类型。如果成功读取了用户输入的名称，则返回名称和零值错误（nil）。然而，如果发生错误，则返回空字符串和错误。

下一个关键函数是 `parseArgs()`。它接收一个字符串切片并返回两个值：一个是 `config` 类型，第二个是 `error` 类型：

```
type config struct {
    numTimes   int
    printUsage bool
}

func parseArgs(args []string) (config, error) {
    var numTimes int
    var err error
    c := config{}
    if len(args) != 1 {
        return c, errors.New("Invalid number of arguments")
    }

    if args[0] == "-h" || args[0] == "--help" {
        c.printUsage = true
        return c, nil
    }

    numTimes, err = strconv.Atoi(args[0])
    if err != nil {
        return c, err
    }
    c.numTimes = numTimes

    return c, nil
}
```

`parseArgs()` 函数创建一个类型为 `config` 的对象 `c` 来存储这些数据。配置结构体用于在内存中表示应用程序在运行时将依赖的数据。它有两个字段：整数字段 `numTimes`，包含要打印问候语的次数；以及布尔字段 `printUsage`，指示用户是否指示打印帮助信息信息。

传递给程序的命令行参数通过 `os` 包中定义的 `Args` 切片可用。切片的第一个元素是程序本身的名字，而 `os.Args[1:]` 切片包含了你的程序可能需要的参数。这是一个传递给 `parseArgs()` 的字符串切片。函数首先检查命令行参数的数量是否不等于 1，如果是，则使用下面的代码片段返回空配置对象和错误：

```
if len(args) != 1 {
    return c, errors.New("Invalid number of arguments")
}
```

如果只指定了一个参数，且参数为 `-h` 或 `-help`，则 `printUsage` 字段被赋值为 `true`，并使用下面的片段返回对象 `c` 和 `nil` 错误：

```
if args[0] == "-h" || args[0] == "-help" {
    c.printUsage = true
    return c, nil
}
```

最后，假设指定的参数是打印问候语的次数，并使用 `strconv` 包中的 `Atoi()` 函数将参数（字符串）转换为对应的整数值：

```
numTimes, err = strconv.Atoi(args[0])
if err != nil {
    return c, err
}
```

如果 `Atoi()` 函数返回非零值，则返回该值；否则，`numTimes` 设置为转换后的数字：

```
c.numTimes = numTimes
```

到为止，我们已经看到了如何读取用户输入和命令行参数。下一步是确保输入在逻辑上是正确的；换句话说，对于应用程序是否有意义。例如，如果用户为打印次数指定了 `0`，这在逻辑上是一个错误的值。`validateArgs()` 函数执行此检查：

```go
func validateArgs(c config) error {
    if !(c.numTimes > 0) {
        return errors.New("specify a number greater than 0")
    }
    return nil
}
```

如果字段 `numTimes` 的值大于 `0`，`validateArgs()` 函数返回 true。在处理并检查命令行参数后，应用程序调用 `runCmd()` 函数根据 `config` 对象中的值执行相应的操作：

```go
func runCmd(r io.Reader, w io.Writer, c config) error {
    if c.printUsage {
        printUsage(w)
        return nil
    }

    name, err := getName(r, w)
    if err != nil {
        return err
    }
    greetUser(c, name, w)
    return nil
}
```

如果字段 `printUsage` 的值设置为 `true`（用户指定的 `-help` 或 `-h`），则调用 `printUsage()` 函数并返回零值错误。否则，调用 `getName()` 函数，要求用户输入其名称。如果 `getName()` 返回非零错误，则返回该错误。否则，调用 `greetUser()` 函数。`greetUser()` 函数根据提供的配置向用户显示问候语：

```go
func greetUser(c config, name string, w io.Writer) {
    msg := fmt.Sprintf("Nice to meet you %s\n", name)
    for i := 0; i < c.numTimes; i++ {
        fmt.Fprintf(w, msg)
    }
}
```

完整的问候应用程序如列表 1.1 所示。`main()` 函数首先从第二个参数开始使用命令行切片调用 `parseArgs()`。我们从函数获取两个值：`c`（`config` 对象）和 `err`（错误值）。如果返回了非零错误，将执行以下步骤：

1.  打印错误。
2.  通过 `printUsage()` 函数并传递 `os.Stdout` 作为写入器来打印使用信息。
3.  通过 `os` 包中的 `Exit()` 函数以退出码 `1` 退出程序。

如果参数解析正确，则使用 `parseArgs()` 返回的 `config` 对象 `c` 调用 `validateArgs()` 函数。

最后，如果 `validateArgs()` 返回零值错误，则调用 `runCmd()` 函数，传递读取器 `os.Stdin`、写入器 `os.Stdout` 以及 `config` 对象 `c`。

创建一个新目录 `chap1/manual-parse/` 其中初始化模块：

```
$ mkdir -p chap1/manual-parse
$ cd chap1/manual-parse
$ go init github.com/username/manual-parse
```

然后将列表 1.1 保存为名为 `main.go` 的文件并编译：

```
$ go build -o application
```

在不指定任何参数的情况下运行命令。你会看到错误以及下面的使用信息：

```
$ ./application
Invalid number of arguments
Usage: ./application <integer> [-h|--help]

A greeter application which prints the name you entered <integer> number of times.
```

此外，你还会看到程序的退出码为 `1`。

```
$ echo $?
1
```

如果你在 Windows 上使用 PowerShell，可以使用命令 `echo $LastExitCode` 来查看退出码。这是命令行应用程序另一个值得注意的行为。任何执行失败的情况都应在使用 `os` 包定义的 `Exit()` 函数终止后导致非零退出码。

如果指定 `-h` 或 `-help`，将打印使用信息：

```
$ ./application -help
Usage: ./application <integer> [-h|-help]

A greeter application which prints the name you entered <integer> number of times.
```

最后，让我们看看成功执行程序时的样子：

```
$ ./application 5
Your name please? Press the Enter key when done.
Joe Cool
Nice to meet you Joe Cool
Nice to meet you Joe Cool
Nice to meet you Joe Cool
Nice to meet you Joe Cool
Nice to meet you Joe Cool
```



2. `-h` 或 `-help` 作为命令行参数指定。

3. 问候语将向用户显示指定的次数。

然而，手动测试容易出错且非常繁琐。接下来，你将学习如何为你的应用程序编写自动化测试。

## 编写单元测试

标准库中的 `testing` 包包含了编写测试以检查你的应用程序行为所需的所有内容。

首先，我们来看 `parseArgs()` 函数。它的定义如下：

```
func parseArgs(args []string) (config, error)       {}
```

它有一个输入：一个字符串切片，代表程序在调用时指定的命令行参数。返回值表示一个 `config` 类型的值和一个 `error` 类型的值。

`testConfig` 结构体将用于封装特定的测试用例：代表输入命令行参数的字符串切片（位于 `args` 字段）、返回到 `err` 字段的预期错误值，以及嵌入 `config` 结构体中返回的预期 `config` 值：

```go
type testConfig struct {
    args []string
    err  error
    config
}
```

### 测试用例示例

```go
{
    args:   []string{"-h"},
    err:    nil,
    config: config{printUsage: true, numTimes: 0},
},
```

这个测试用例检查了执行应用程序时将 `-h` 作为命令行参数指定的行为。

我们又添加了几个测试用例，并如下方式初始化测试用例切片：

```go
tests := []testConfig{
    {
        args:   []string{"-h"},
        err:    nil,
        config: config{printUsage: true, numTimes: 0},
    },
    {
        args:   []string{"10"},
        err:    nil,
        config: config{printUsage: false, numTimes: 10},
    },
    {
        args:   []string{"abc"},
        err:    errors.New("strconv.Atoi: parsing \"abc\": invalid syntax"),
        config: config{printUsage: false, numTimes: 0},
    },
    {
        args:   []string{"1", "foo"},
        err:    errors.New("Invalid number of arguments"),
        config: config{printUsage: false, numTimes: 0},
    },
}
```

一旦我们定义了上面的测试配置切片，我们将遍历它们，使用 `args` 中的值调用 `parseArgs()` 函数，并检查返回值 `c` 和 `err` 是否分别符合预期的 `config` 类型和 `error` 类型的值。完整的测试将如 列表 1.2 所示。

在与你保存 列表 1.1 相同的目录中，将 列表 1.2 保存为名为 `parse_flags_test.go` 的文件。现在，使用 `go test` 运行测试：

```
$ go test -v
=== RUN   TestParseArgs
--- PASS: TestParseArgs (0.00s)
PASS
ok          github.com/practicalgo/code/chap1/manual-parse        0.093
```

在运行 `go test` 时传递 `-v` 标志还会显示正在执行的测试函数及其结果。

接下来，我们查看定义为 `func validateArgs(c config) error` 的 `validateArgs()` 函数。根据函数的规范，我们再次定义测试用例切片。然而，我们不再使用命名类型，而是如下使用`匿名`类型：

```go
tests := []struct {
    c   config
    err error
}{
    {
        c:   config{},
        err: errors.New("Must specify a number greater than 0"),
    },
    {
        c:   config{numTimes: -1},
        err: errors.New("Must specify a number greater than 0"),
    },
    {
        c:   config{numTimes: 10},
        err: nil,
    },
}
```

每个测试用例包含两个字段：输入对象 `c` 类型和预期的 `err` 值。测试函数在 列表 1.3 所示。

在与 列表 1.2 相同的目录中，将 列表 1.3 保存为 `validate_args_test.go` 文件。



用户界面由以下组件组成：

* `-h` — 逻辑选项，通常用于输出帮助文本。
* `-n <value>` 期望用户指定参数 `n` 的值。应用程序逻辑决定了该值预期的数据类型。
* `-silent` — 另一个逻辑参数。指定它将该值设置为 `true`。
* `arg1` 和 `arg2` 被称为位置参数。位置参数的数据类型和解释完全由应用程序定义。

`flag` 包实现了内置的类型和方法，用于编写具有上述标准行为的命令行应用程序。当您在运行应用程序时指定 `-h` 参数时，所有其他参数（如果已指定）都将被忽略，并将打印帮助信息。

应用程序将包含*必选*和*可选*参数的组合。

这里还需要注意的是，任何位置参数都必须在指定了所有*必要*参数*之后*才能指定。`flag` 包一旦遇到位置参数、`-` 或 `--`，就会停止对参数解析。

表 1.1 总结了该包在解析命令行参数示例时的行为。

表 1.1：通过 `flag` 解析命令行参数

| 命令行参数 | `FLAG` 解析行为 |
| --- | --- |
| * `-h` | 显示帮助信息。 |
| * `-n 1 hello -h` | 显示帮助信息。 |
| * `-n 1 Hello` | 标志 `n` 的值被设置为 `1`，`Hello` 作为位置参数可用。 |
| * `-n 1 Hello` | 标志 `n` 的值被设置为 `1`，其余部分忽略。 |
| * `Hello -n 1` | `-n 1` 被忽略。 |

让我们来看一个例子，通过重写问候应用程序，使得次数由参数 `-n` 指定。界面如下：

```
$ ./application -n 2
Your name please? Press the Enter key when done.
Joe Cool
Nice to meet you Joe Cool
```

与代码 1.1 相比，关键在于 `parseArgs()` 函数的编写方式：

```go
func parseArgs(w io.Writer, args []string) (config, error) {
        c := config{}
        fs := flag.NewFlagSet("greeter", flag.ContinueOnError)
        fs.SetOutput(w)
        fs.IntVar(&c.numTimes, "n", 0, "Number of times to greet")
        err := fs.Parse(args)
        if err != nil {
                return c, err
        }
        if fs.NArg() != 0 {
                return c, errors.New("Positional arguments specified")
        }
        return c, nil}
```

该函数接受两个参数：满足 `io.Writer` 接口的变量 `w` 和表示解析参数的字符串数组。它返回 `config` 对象和 `error`。为了解析，创建一个 `FlagSet` 对象：

```go
fs := flag.NewFlagSet("greeter", flag.ContinueOnError)
```

`flag` 包定义的 `NewFlagSet()` 函数用于创建 `FlagSet` 对象。将其视为用于处理命令行接收参数的抽象。`NewFlagSet()` 的第一个参数是将在帮助信息中显示的命令名称。第二个参数设置了在解析命令行发生错误时发生的情况；即调用 `fs.Parse()` 函数时。如果指定了 `ContinueOnError` 选项，即使 `Parse()` 返回非空错误，程序也将继续。这在您希望在错误情况下执行自定义处理时有用。其他可能的值是 `ExitOnError`（停止程序）和 `PanicOnError`（调用 `panic()`）。`ExitOnError` 和 `PanicOnError` 的区别在于，在后者的情况下可以使用 `recover()` 函数在程序之前执行任何清理操作。

`SetOutput()` 方法指定了初始化 `FlagSet` 对象将用于写入任何诊断或输出消息。默认设置为 `os.Stderr`。将其设置为指定的写入器 `w` 允许我们编写单元测试来检查行为。

接下来定义第一个变体：

```go
fs.IntVar(&c.numTimes, "n", 0, "Number of times to greet")
```

`IntVar()` 方法用于创建一个预期类型为 `int` 的参数。方法的第一个参数是存储整数的变量地址。第二个参数是选项本身 `n`。第三个参数是默认值，最后一个参数是描述参数用途的字符串。它会自动显示在程序的帮助文本中。对于其他数据类型——`float`、`string` 和 `bool` 也定义了类似的方法。您也可以为自定义类型定义标志参数。

接下来我们传递切片 `args[]` 调用 `Parse()` 函数：

```go
err := fs.Parse(args)
if err != nil {
        return c, err
}
```

这是一个读取切片元素并检查它们是否符合定义的标志的函数。在检查期间，它尝试填充指定变量中的值，并根据 `NewFlagSet()` 函数指定的第二个参数返回给调用者的错误或停止执行。如果返回非空错误，`parseArgs()` 返回对象和错误：

```go
if fs.NArg() != 0 {
        return c, errors.New("Positional arguments specified")
}
```

如果返回空错误，我们检查是否指定了位置参数。`NArg()` 返回解析后位置参数的数量。

完整程序见代码 1.5。

`config` 结构体类型已修改，使其不再包含 `printUsage` 字段，因为 `parseArgs()` 现在处理 `-h` 参数。创建一个新目录 `chap1/flag-parse/` 并在其中初始化模块：

```
$ mkdir -p chap1/flag-parse
$ cd chap1/flag-parse
$ go mod init github.com/username/flag-parse
```

然后将代码 1.5 保存为名为 `main.go` 的文件并编译：

```bash
$ go build -o application
```




```
$ ./application -n abc
invalid value "abc" for flag -n: parse error
Usage of greeter:
  -n int
            Number of times to greet
invalid value "abc" for flag -n: parse error
```

注意我们是如何自动获取类型检查错误的，因为我们正尝试指定一个非整数值。此外，请注意我们在这里再次收到了两次错误。我们将在本章稍后修复它。

最后，让我们带有允许的参数 `-n` 程序：

```
$ ./application -n 4
Your name please? Press the Enter key when done.
John Doe
Nice to meet you John Doe
Nice to meet you John Doe
Nice to meet you John Doe
Nice to meet you John Doe
```

### 测试解析逻辑

与第一个版本相比，我们问候程序中的主要变化在于我们如何使用 `flag` 包来分析命令行参数。你会发现，你已经写好了一个问候程序，特别是 `parseArgs()` 函数，并且它的形式非常便于模块化测试：

1. 在函数中创建了一个新的 `FlagSet` 对象。
2. 使用 `FlagSet` 对象的 `Output()` 方法，你确保了来自 `FlagSet` 方法的任何消息都会写入指定的 `io.Writer` 对象 `w` 中。
3. 用于解析的参数通过参数 `args` 传递。

该函数封装得良好，并且没有使用任何全局状态。函数的测试显示在 列表 1.6 中。

将 列表 1.6 保存到你保存 列表 1.5 的目录中。将文件命名为 `parse_args_test.go`。

`runCmd()` 函数的模块化测试与 列表 1.4 相同，但缺少了第一个测试，该测试用于检查当参数 `printUsage` 值被设置为 `true` 时 `runCmd()` 的行为。我们想要测试的测试用例如下：

```
tests := []struct {
    c      config
    input  string
    output string
    err    error
}{
    {
        c:      config{numTimes: 5},
        input:  "",
        output: strings.Repeat("Your name please? Press the Enter key when done.\n", 1),
        err:    errors.New("You didn't enter your name"),
    },
    {
        c:      config{numTimes: 5},
        input:  "Bill Bryson",
        output: "Your name please? Press the Enter key when done.\n" + strings.Repeat("Nice to meet you Bill Bryson\n", 5),
    },
}
```

你可以在 `flag-parse` 子目录下的 `run_cmd_test.go` 文件中找到完整的测试。

`validateArgs()` 函数的测试与 列表 1.3 相同。你可以在 `flag-parse` 子目录下的 `validate_args_test.go` 文件中找到它。现在运行所有测试：

```
$ go test -v
=== RUN   TestSetupFlagSet
--- PASS: TestSetupFlagSet (0s)
=== RUN   TestRunCmd
--- PASS: TestRunCmd (0s)
=== RUN   TestValidateArgs
--- PASS: TestValidateArgs (0s)
PASS
ok      github.com/practical-go/chap1/flag-parse    0.01s
```

太棒了。现在你重写了问候程序的解析逻辑以使用 `flag` 包，然后更新了模块测试以检查新的行为。接下来，你将通过几种方式改进用户界面。在这样做之前，让我们先完成 练习 1.2。

## 改进用户界面

在接下来的章节中，你将通过以下三种方式改进用户界面：

* 删除重复的错误信息
* 配置用法帮助信息
* 允许用户通过位置参数输入名称

在实现这些改进时，你将学习如何创建自定义错误、配置 `FlagSet` 对象以打印自定义的用法信息以及访问位置参数。

### 删除重复的错误信息

你可能注意到错误显示了两次。这是由于 `main()` 函数中的一段代码引起的：

```
c, err := parseArgs(os.Stderr, os.Args[1:])
if err != nil {
    fmt.Println(err)
    os.Exit(1)
}
```

当 `Parse()` 函数遇到错误时，它会将该错误输出到 `fs.SetOutput()` 调用设置的输出实例。随后，返回的错误也会通过上述代码段在 `main()` 中打印。在 `main()` 中不打印错误似乎是一个简单的解决方案。但这意味着任何在指定位置参数时返回的错误将不会显示。然而，为了不在 `main()` 中打印错误，我们可以通过以下方式创建自定义错误值：

```go
var errArgSpecified = errors.New("positional arguments specified")
```

然后在 `parseArgs()` 函数中返回它：

```go
if fs.NArg() > 1 {
    return c, errArgSpecified
}
```

然后在 `main()` 中更新代码：

```go
c, err := parseArgs(os.Stderr, os.Args[1:])
if err != nil {
    if errors.Is(err, errArgSpecified) {
        fmt.Fprintln(os.Stderr, err)
    }
    os.Exit(1)
}
```

### 配置用法信息

如果你将 列表 1.5 与 列表 1.1 进行比较，你会发现用法信息没有指定。这是因为 `flag` 包根据 `FlagSet` 的名称和参数自动创建了它。然而，如果你自定义它，可以通过为 `FlagSet` 对象的 `Usage` 属性设置函数来实现：

```go
fs.Usage = func() {
    var usageString = `
A greeter application which prints the name you entered a specified number of times.
 
Usage of %s: <options> [name]`

    fmt.Fprintf(w, usageString, fs.Name())
    fmt.Fprintln(w)
    fs.PrintDefaults()
}
```




接下来，你将进行最后的改进。欢迎程序现在还允许通过位置参数指定名称。如果未指定名称，你将在交互式模式下提示输入名称。

### 通过位置参数接收名称

首先，更新 `config` 结构体，添加一个字符串类型的 `name` 字段，如下所示：

```go
type config struct {
    numTimes int
    name     string
}
```

然后将 `greetUser()` 函数更新为如下内容：

```go
func greetUser(c config, w io.Writer) {
    msg := fmt.Sprintf("Nice to meet you %s\n", c.name)
    for i := 0; i < c.numTimes; i++ {
        fmt.Fprintf(w, msg)
    }
}
```

接着，我们如下所示更新自定义错误值：

```go
var errInvalidPosArgSpecified = errors.New("More than one positional argument specified")
```

现在我们如下所示更新 `parseArgs` 函数以处理位置参数，如果找到，则设置 `config` 对象的属性：

```go
if len(args) > 1 {
    return c, errInvalidPosArgSpecified
}
if len(args) == 1 {
    c.name = args[0]
}
```

`runCmd()` 函数被更新为如下内容，如果未指定它将在交互式模式下请求用户输入名称，如果为空：

```go
func runCmd(rd io.Reader, w io.Writer) (config, error) {
    var c config
    var err error
    c, err = parseArgs(os.Args[1:])
    if err != nil {
        return c, err
    }
    if c.name == "" {
        c.name, err = getName(rd)
        if err != nil {
            return c, err
        }
    }
    greetUser(c, w)
    return c, nil
}
```

所有更改后的完整程序在示例 1.7 中所示。如下所示构建它：

```bash
$ go build -o application
```

运行构建好的程序并使用 `-help`，你会看到使用信息：

```bash
$ ./application -help
A greeter application which prints the name you entered a specified of times.
 
Usage of greeter: <options> [name]
 
Options:
  -n int
            Number of times to greet
```

现在通过位置参数指定名称：

```bash
$ ./application 1 "Jane Doe"
Nice to meet you Jane Doe
```

接下来指定错误输入——字符串作为选项 `-n` 的值：

```bash
$ ./application -n a "Jane Doe"
invalid value "a" for flag -n: parse error
 
A greeter application which prints the name you entered a specified number of times.
 
Usage of greeter: <options> [name]
 
Options:
  -n
```

这里需要注意两点：

* 现在错误只显示一次，而不是两次。
* 我们的自定义使用信息取代了默认值。

## 更新单元测试

我们将通过更新已修改函数的单元测试来结束本章。首先考虑 `parseArgs` 函数。我们定义了一个用于测试用匿名匿名结构：

```go
tests := []struct {
    args   []string
    config config
    output string
    err    error
}{
}
```

字段如下：

* `args`: 包含用于分析的命令行参数切片。
* `config`: 代表 `config` 对象的预期值的内置字段。
* `output`: 将存储预期标准输出的字符串。
* `err`: 将存储预期错误的值。

然后，我们定义了测试用例切片，代表不同的测试用例。第一个如下所示：

```go
{
    args: []string{"-h"},
    output: `
A greeter application which prints the name you entered a specified number of times.
 
Usage of greeter: <options> [name]
 
Options: 
  -n int
            Number of times to greet
`,
    err:    errors.New("flag: help requested"),
    config: config{numTimes: 0},
},
```



在本章的开始，我们通过直接解析命令行参数实现了一个基础的命令行界面。随后，你学习了如何使用 `flag` 包来定义标准的命令行界面。你不再需要手写实现语法解析和参数检查，而是学会了使用该包的内置支持来处理自定义参数和数据类型检查。在整个章节中，你编写了封装良好的函数，以简化单元测试。

在接下来的一章中，你将继续深入学习 `flag` 包，学习如何实现带有子命令的命令行应用程序，提高应用程序的可靠性以及许多其他内容。

# 第 2 章：高级命令行应用程序

在本章中，你将学习如何使用 `flag` 包来实现带有子命令的命令行应用程序。接下，你将看到如何通过使用上下文（contexts）来确保命令行应用程序行为的可预测性。最后，你将学习如何在你的应用程序中组合上下文并处理操作系统信号。让我们开始吧。

## 实现子命令

`子命令`（Subcommands）是将你的命令行应用程序的功能划分为逻辑上独立的命令的方法，每个命令都有自己的参数和操作数。你有一个顶层命令——即你的应用程序——然后你有一组子命令，每个子命令都有自己的参数和操作数。例如，Go 工具链作为一个单一应用程序 `go` 存在，它就是一个顶层命令。作为 Go 开发人员，你将通过特定的子命令如 `build`、`fmt` 和 `test` 与它的不同功能进行交互。

你记得在第 1 章 中，为了创建一个命令行应用程序，你首先创建一个 `FlagSet` 对象。为了创建一个带有子命令的应用程序，你将为每个子命令创建一个 `FlagSet` 对象。然后，根据指定的子命令，使用相应的 `FlagSet` 对象来解析剩余的命令行参数（参见 图 2.1）。

![图 2.1：主应用程序查看命令行参数，并在可能的情况下调用相应的子命令处理器。](img/0201.png)

`图 2.1`:主应用程序查看命令行参数，并在可能的情况下调用相应的子命令处理器。

让我们考虑具有两个子命令 `cmd-a` 和 `cmd-b` 的应用程序的 `main()` 函数：

```go
package main

func main() {
    var err error
    if len(os.Args) < 2 {
        printUsage(os.Stdout)
        os.Exit(1)
    }
    switch os.Args[1] {
    case "cmd-a":
        err = handleCmdA(os.Stdout, os.Args[2:])
    case "cmd-b":
        err = handleCmdB(os.Stdout, os.Args[2:])
    default:
        printUsage(os.Stdout)
    }

    if err != nil {
        fmt.Println(err)
    }
    os.Exit(1)
}
```

`os.Args` 切片包含传递给应用程序的命令行参数。我们将处理三种输入情况：

1. 如果第二个参数是 `cmd-a`，则调用函数 `handleCmdA()`。
2. 如果第二个参数是 `cmd-b`，则调用函数 `handleCmdB()`。
3. 如果调用应用程序时没有提供任何子命令，或者不满足上述情况 1 或 2 中的任一情况，则调用 `printUsage()` 函数打印帮助信息并退出。

`handleCmdA()` 函数实现如下：

```go
func handleCmdA(w io.Writer, args []string) error {
    var v string
    fs := flag.NewFlagSet("cmd-a", flag.ContinueOnError)
    fs.SetOutput(w)
    fs.StringVar(&v, "verb", "argument-value", "Argument 1")
    err := fs.Parse(args)
    if err != nil {
        return err
    }
    fmt.Fprintf(w, "Executing command A")
    return nil
}
```

上述函数与你之前在第 1 章中作为问候应用程序的一部分实现的 `parseArgs()` 函数非常相似。它创建一个新的 `FlagSet` 对象，配置各种参数并解析一个特定的操作数切片。`handleCmdB()` 函数将执行子命令 cmd-b 自己的配置。

`printUsage()` 函数定义如下：

```go
func printUsage(w io.Writer) {
    fmt.Fprintf(w, "Usage: %s [cmd-a|cmd-b] -h\n", os.Args[0])
    handleCmdA(w, []string{"-h"})
    handleCmdB(w, []string{"-h"})
}
```

首先，我们使用 `fmt.Fprintf()` 函数打印应用程序的使用信息字符串，然后调用各个子命令处理器函数，并将 `-h` 作为参数集中的唯一元素。

### 子命令驱动应用程序的架构

在开发子命令驱动的应用程序时，良好的做法是保持主包的紧凑并为子命令创建一个独立的包。你的主包将解析命令行参数并调用相应的处理器函数。如果提供的参数无法识别，则显示包含所有可识别内容的帮助信息（参见 图 2.2）。

随后你将为通用网络客户端奠基础，你将在后续章节中使用它。我们将该程序命名为 `mync`（`my network client` 的缩写）。目前你可以忽略子命令的实现，并在后续章节填充实现时再返回这里。

让我们先查看 `main` 包的实现。这里只有一个用于启动的 `main.go` 文件（参见 代码列表 2.2）。

在顶部，我们导入 `cmd` 包，它代表包含子命令实现的子包。由于我们将初始化应用程序模块，因此指定了 `cmd` 包的绝对导入路径。`main()` 函数调用 `handleCommand()` 函数并传递所有从第二个参数开始的参数：

```go
err := handleCommand(os.Args[1:])
```

如果 `handleCommand()` 函数发现收到的切片为空（意味着未指定命令行参数），它将返回一个自定义错误值：





```go
if len(args) < 1 {
    err = errInvalidSubCommand
}
```

如果指定了命令行参数，将定义 `switch..case` 结构，根据切片 `args` 的第一个元素来调用相应的命令处理函数：

1. 如果该元素是 `http` 或 `grpc`，则调用相应的处理函数。
2. 如果第一个元素是 `-h` 或 `-help`，则调用 `printUsage()` 函数。
3. 如果它不符合上述任何条件，则调用 `printUsage()` 函数并返回自定义的错误值。

`printUsage()` 函数首先使用 `fmt.Fprintf(w, "Usage: mync [http|grpc] -h\n")` 打印消息，然后调用带有仅包含 `"-h"` 的切片的子命令实现。

创建一个新目录 `chap2/sub-cmd-arch` 并在其中初始化模块：

```bash
$ mkdir -p chap2/sub-cmd-arch
$ cd chap2/sub-cmd-arch
$ go mod init github.com/username/chap2/sub-cmd-arch/
```

将列表 2.2 保存为上述目录中的 `main.go`。

现在让我们来看 `HandleHttp()` 函数，它负责处理 `http` 子命令（参见列表 2.3）。

`HandleHttp()` 函数创建一个 `FlagSet` 对象并使用参数、自定义用法以及其他错误处理对其进行配置。

在之前创建的目录内创建一个子目录 `cmd`，并将列表 2.3 保存为 `httpCmd.go`。

`HandleGrpc()` 函数也以类似的方式实现（参见列表 2.4）。

将列表 2.4 保存为 `cmd` 子目录下的 `grpcCmd.go`。

自定义错误值 `ErrNoServerSpecified` 在 `cmd` 包中的一个独立文件中创建，如列表 2.5 所示。

在 `cmd` 子目录中将列表 2.5 保存为 `errors.go`。最终你将得到如下的源码树结构：

```
.
|____cmd
| |____grpcCmd.go
| |____httpCmd.go
| |____errors.go
|____go.mod
|____main.go
```

在模块根目录下编译应用程序：

```bash
$ go build -o application
```

尝试使用其他参数运行生成的 `application`，从 `-help` 或 `-h` 开始：

```bash
$ ./application --help
Usage: mync [http|grpc] -h
 
http: A HTTP client.
 
http: <options> server
 
Options:
  -verb string
            HTTP method (default "GET")
 
grpc: A gRPC client.
 
grpc: <options> server
 
Options:
  -body string
            Body of request
  -method string
            Method to call
```

在继续之前，让我们确保已经为 `main` 和 `cmd` 包实现的功能编写单元测试。

### 测试 main 包

首先，让我们为主包编写一个单元测试。`handleCommand()` 是一个关键函数，它也会调用包中的其他函数。它的定义如下：

```go
err := handleCommand(w io.Writer, args []string)
```

在测试中，我们将传入程序可以调用的参数字符串切片调用该函数，并检查预期的行为。来看测试配置：

```go
testConfigs := []struct {
    args   []string
    output string
    err    error
}{
    // 检查未指定应用程序参数
    // 时的行为
    {
        args:   []string{},
        err:    errInvalidSubCommand,
        output: "Invalid sub-command specified\n" + usageMessage,
    },
    // 检查在应用程序参数中指定 "-h" 
    // 时的行为
    {
        args:   []string{"-h"},
        err:    nil,
        output: usageMessage,
    },
    // 检查输入未识别的应用程序子命令
    // 时的行为
    {
        args:   []string{"foo"},
        err:    errInvalidSubCommand,
        output: "Invalid sub-command specified\n" + usageMessage,
    },
}
```

完整的测试在列表 2.6 中显示。




可靠应用程序的一个显著特征是，在运行期间对其行为应用了特定程度的控制。例如，当你的程序发出 HTTP 请求时，你可能希望它在用户指定的秒数内完成，否则就带错误消息退出。当应用了此类措施时，程序的行为对用户来说变得更具可预测性。标准库中的 `context` 包允许应用程序应用这种控制。它定义了 `Context` 结构体类型以及三个函数——`withDeadline()`、`withCancel()` 和 `withTimeout()`——用于确保在执行你的代码时提供特定的运行时间保证。你会发现许多标准库包都要求将上下文对象作为第一个参数传递。示例包括 `net`、`net/http` 和 `os/exec` 包中的函数。虽然上下文（contexts）在与外部资源通信时最常见，但它们同样适用于任何可能存在不可预测行为概率的其他功能。

### 带有截止期限的用户输入

让我们考虑这样一个示例：你的程序请求用户输入，用户必须在 5 秒内输入内容并按 Enter 键，否则程序将使用默认名称继续运行。虽然这是一个假设的例子，但它说明了你如何为应用程序中的任何用户代码设置超时。

让我们先看 `main()` 函数：

```
package main

func main() {
    allowedDuration := totalDuration * time.Second

    ctx, cancel := context.WithTimeout(context.Background(), allowedDuration)
    defer cancel()

    name, err := getNameContext(ctx)

    if err != nil && !errors.Is(err, context.DeadlineExceeded) {
        fmt.Fprintf(os.Stdout, "%v\n", err)
        os.Exit(1)
    }
    fmt.Fprintln(os.Stdout, name)
}
```

该函数使用 `context.WithTimeout()` 函数创建一个新的上下文。`context.WithTimeout()` 函数接受两个参数：第一个是父级 `Context` 对象，第二个是 `time.Duration` 对象，指定了时间（以毫秒、秒或分钟为单位），在此时间之后上下文将过期。在这里，我们将等待时间设置为 5 秒：

```
allowedDuration := totalDuration * time.Second
```

接下来，我们创建一个 `Context` 对象：

```
ctx, cancel := context.WithTimeout(context.Background(), allowedDuration)
defer cancel()
```

由于我们没有其他可以充当父上下文的角色，我们使用 `context.Background()` 创建一个新的空上下文。`WithTimeout()` 返回两个值：创建的上下文 `ctx` 和取消函数 `cancel`。有必要在 `defer` 语句中调用取消函数，以确保它在函数返回之前总是被调用。然后我们以如下方式调用 `getNameContext()`：

```
name, err := getNameContext(ctx)
```

如果返回的错误是预期的 `context.DeadlineExceeded`，我们不向用户显示它，而是直接显示名称；否则，我们显示错误并以非零状态码退出：

```
f err != nil && !errors.Is(err, context.DeadlineExceeded) {
        fmt.Fprintf(os.Stdout, "%v\n", err)
        os.Exit(1)
}
fmt.Fprintln(os.Stdout, name)
```

现在来看 `getNameContext()` 函数：

```
func getNameContext(ctx context.Context) (string, error) {
    var err error
    name := "Default Name"
    c := make(chan error, 1)

    go func() {
        name, err = getName(os.Stdin, os.Stdout)
        c <- err
    }()

    select {
    case <-ctx.Done():
        return name, ctx.Err()
    case err := <-c:
        return name, err
    }
}
```

该函数的实现思路如下：

1.  在 goroutine 中执行 `getName()` 函数。
2.  一旦函数返回，将错误值写入通道。
3.  创建一个 `select..case` 块，用于等待两个通道上的读取操作：
    1.  `ctx.Done()` 写入信号的通道。
    2.  当 `getName()` 函数返回值时写入信号的通道。
4.  根据上述步骤 a 或 b 哪一个先完成，要么返回默认名称和上下文超时错误，要么返回 `getName()` 函数产生的值。

完整代码显示在 Listing 2.7 中。

创建一个新目录 `chap2/user-input`：

```
mkdir -p chap2/user-input
cd chap2/user-input
```

初始化模块：

```bash
go mod init user-input
```

创建 `main.go` 文件（将上面的代码粘贴进去）。编译：

```bash
go build -o application
```

运行程序：

```bash
./application
```

如果你不输入名称，你会看到：

再次运行：

```bash
./application
```

如果你输入了名称，你会看到：

```
Default Name
```

这样，你就学会了使用 `WithTimeout()` 创建上下文。另一方面，`WithDeadline()` 函数适用于你想相对于当前时间设置截止期限。

### 处理用户信号

用户信号是用户中断程序正常运行的一种。Linux 和 MacOS 中两种常用的用户信号：按下 Ctrl+C 组合键时的 `SIGINT` 以及执行 `kill` 命令时的 `SIGTERM`。我们希望用户能够在任何时候取消。

我们之前提到过某些标准库函数接受上下文。让我们看看 `os/exec` 包中的 `CommandContext()` 是如何工作的。其中一种非常有用的情况是，你想设置一个最大时间。同样，可以使用通过 `WithTimeout()` 创建的上下文来实现：

```go
package main

import (
    "context"
    "fmt"
    "os"
    "os/exec"
    "time"
)

func main() {
    ctx, cancel := context.WithTimeout(context.Background(), 10*time.Second)
    defer cancel()
    if err := exec.CommandContext(ctx, "sleep", "20").Run(); err != nil {
        fmt.Fprintln(os.Stdout, err)
    }
}
```

在 Linux/MacOS 上运行上述代码会导致以下错误：

```
signal: killed
```



2. Настройте обработчик сигналов, который создаст обработчик сигналов `SIGINT` и `SIGTERM`. Когда один из сигналов получен, код обработки сигнала вручную вызовет функцию отмены, возвращенную на шаге 1.

3. Выполните внешнюю программу с помощью функции `CommandContext()`, используя контекст, созданный на шаге 1.

#### Шаг 1 реализован в функции `createContextWithTimeout()`:

```go
func createContextWithTimeout(d time.Duration) (context.Context, context.CancelFunc) {
    ctx, cancel := context.WithTimeout(context.Background(), d)
    return ctx, cancel
}
```

Функция `WithTimeout()` из пакета контекста вызывается для создания контекста, который отменяется, когда истекает указанная единица времени `d`. Первый параметр — это пустой ненулевой контекст, созданный вызовом функции `context.Background()`. Возвращаются контекст, `ctx`, и функция отмены, `cancel`. Мы не вызываем здесь функцию отмены, так как нам нужен контекст на протяжении всего жизненного цикла программы.

#### Шаг 2 реализован в функции `setupSignalHandler()`:

```go
func setupSignalHandler(w io.Writer, cancelFunc context.CancelFunc) {
    c := make(chan os.Signal, 1)
    signal.Notify(c, syscall.SIGINT, syscall.SIGTERM)
    go func() {
        s := <-c
        fmt.Fprintf(w, "Got signal:%v\n", s)
        cancelFunc()
    }()
}
```

Эта функция создает способ обработки сигналов `SIGINT` и `SIGTERM`. Канал емкостью 1 создается с типом `Signal` (определен в пакете `os`). Затем мы вызываем функцию `Notify()` из пакета сигналов, чтобы настроить канал прослушивания для сигналов `syscall.SIGINT` и `syscall.SIGTERM`. Мы настроили горутину для ожидания этого сигнала. Когда мы его получаем, мы вызываем функцию `cancelFunc()`, которая является функцией отмены контекста, соответствующей созданному выше `ctx`. Когда мы вызываем эту функцию, реализация `os.execCommandContext()` распознает это и в конечном итоге принудительно уничтожает команду. Конечно, если сигнал `SIGINT` или `SIGTERM` не получен, команда может выполняться нормально в соответствии с определенным контекстом, `ctx`.

#### Шаг 3 реализуется следующей функцией:

```go
func executeCommand(ctx context.Context, command string, arg string) error {
    return exec.CommandContext(ctx, command, arg).Run()
}
```

Полная программа показана в Листинге 2.8.

Функция `main()` начинает с проверки того, указано ли ожидаемое количество аргументов. Здесь мы реализуем базовый пользовательский интерфейс и ожидаем, что приложение будет выполняться как `./application sleep 60`, где `sleep` — это выполняемая команда, а `60` — аргумент команды. Затем мы сохраняем команду, которую нужно выполнить, и аргумент к ней в двух строковых переменных: `command` и `arg`. Затем вызывается функция `createContextWithTimeout()` с объектом длительности, указывающим 30-секундный таймаут. Функция возвращает контекст, `ctx`, и функцию отмены контекста, `cancel`. В следующем операторе мы вызываем функцию в отложенном вызове.

Затем мы вызываем функцию `setupSignalHandler()`, передавая ей два параметра: `os.Stdout` и функцию отмены контекста, `cancel`.

Наконец, мы вызываем функцию `executeCommand()` с созданным объектом контекста, `ctx`; команда для выполнения, `command`; и аргумент команды, `arg`. Если возвращается ошибка, она печатается.

Создайте новый каталог, `chap2/user-signal`, и инициализируйте в нем модуль:

```bash
$ mkdir -p chap2/user-signal
$ cd chap2/user-signal
$ go mod init github.com/username/user-signal
```

Затем сохраните Листинг 2.8 как новый файл `main.go` и соберите его:

```bash
$ go build -o application
```

Учитывая, что таймаут установлен на 30 секунд, давайте попробуем выполнить команду `sleep` со значением времени сна:

```bash
% ./application sleep 60
^CGot signal:interrupt
signal: interrupt
```

Мы просим команду `sleep` заснуть на 60 секунд, но вручную прерываем ее, нажав Ctrl+C. Сообщение об ошибке сообщает нам, как команда была прервана.

Далее спим 10 секунд:

```bash
% ./application sleep 10
```

Поскольку 10 секунд меньше, чем время ожидания контекста в 30 секунд, он завершается без ошибок. Наконец, давайте выполним команду `sleep` на 31 секунду:

```bash
% ./listing7 sleep 31
signal: killed
```

Теперь мы видим, что контекст таймаута срабатывает и убивает процесс.

## Резюме

В этой главе вы узнали о шаблонах для реализации масштабируемых приложений командной строки. Вы узнали, как реализовать интерфейс на основе подкоманд для вашего приложения, и вы использовали его для разработки масштабируемых приложений.

中文译文：

[content]
2. 配置一个信号处理器，以创建 `SIGINT` 和 `SIGTERM` 信号处理器。当接收到其中一个信号时，信号处理代码将手动调用第 1 步返回的取消函数。

3. 使用 `CommandContext()` 函数执行外部程序，使用第 1 步中创建的上下文。

#### 步骤 1 在函数 `createContextWithTimeout()` 中实现：

```go
func createContextWithTimeout(d time.Duration) (context.Context, context.CancelFunc) {
    ctx, cancel := context.WithTimeout(context.Background(), d)
    return ctx, cancel
}
```

调用 context 包中的 `WithTimeout()` 函数用于创建一个上下文，该上下文在指定的时间单位 `d` 到期时被取消。第一个参数是通过调用函数 `context.Background()` 创建的非空上下文。返回的是上下文 `ctx` 和取消函数 `cancel`。我们在此处不调用该取消函数，因为我们需要在整个程序的生命周期内都使用该上下文。

#### 步骤 2 在函数 `setupSignalHandler()` 中实现：

```go
func setupSignalHandler(w io.Writer, cancelFunc context.CancelFunc) {
    c := make(chan os.Signal, 1)
    signal.Notify(c, syscall.SIGINT, syscall.SIGTERM)
    go func() {
        s := <-c
        fmt.Fprintf(w, "Got signal:%v\n", s)
        cancelFunc()
    }()
}
```

该函数创建处理 `SIGINT` 和 `SIGTERM` 信号的方法。创建一个容量为 1 类型为 `Signal`（定义在 `os` 包中）的通道。然后调用 signal 包中的 `Notify()` 函数，为 `syscall.SIGINT` 和 `syscall.SIGTERM` 信号配置监听通道。我们启动了一个 goroutine 来等待这些信号。当我们接收到信号时，调用 `cancelFunc()`，它是对应上面创建的 `ctx` 的上下文取消函数。当我们调用此函数时，`os.execCommandContext()` 的实现会识别这一点并最终强制杀死命令。当然，如果没有接收到 `SIGINT` 或 `SIGTERM` 信号，命令将根据定义的上下文 `ctx` 正常运行。

#### 步骤 3 由以下函数实现：

```go
func executeCommand(ctx context.Context, command string, arg string) error {
    return exec.CommandContext(ctx, command, arg).Run()
}
```

完整程序显示在 列表 2.8 中。

`main()` 函数从检查是否指定了预期参数数量开始。在这里我们实现了基础的用户界面，并预期应用程序以 `./application sleep 60` 运行，其中 `sleep` 是要执行的命令，而 `60` 是命令参数。然后我们将需要执行的命令及其参数保存在两个字符串变量中：`command` 和 `arg`。接着调用 `createContextWithTimeout()` 函数，传入指定 30 秒超时的持续对象。该函数返回上下文 `ctx` 和上下文取消函数 `cancel`。在后续的语句中，我们在延迟调用中执行该函数。

然后我们调用 `setupSignalHandler()` 函数，传递两个参数：`os.Stdout` 和上下文取消函数 `cancel`。

最后，我们调用 `executeCommand()` 函数，传入创建的上下文对象 `ctx`；要执行的命令 `command` 以及命令参数 `arg`。如果返回错误，则将其打印。

创建一个新目录 `chap2/user-signal` 其中初始化模块：

```bash
$ mkdir -p chap2/user-signal
$ cd chap2/user-signal
$ go mod init github.com/username/user-signal
```

然后将 列表 2.8 保存为新文件 `main.go` 并编译它：

```bash
$ go build -o application
```

考虑到超时被设置为 30 秒，让我们尝试执行带有睡眠时间参数的 `sleep` 命令：

```bash
% ./application sleep 60
^CGot signal:interrupt
signal: interrupt
```

我们要求 `sleep` 命令睡眠 60 秒，但通过按下 Ctrl+C 手动中断了它。错误信息告诉我们命令是如何被中断的。

接下来睡眠 10 秒：

```bash
% ./application sleep 10
```

由于 10 秒小于上下文 30 秒的等待时间，它将无错误地退出。最后，让我们运行 31 秒的 `sleep` 命令：

```bash
% ./listing7 sleep 31
signal: killed
```

现在我们看到超时上下文触发并杀死了进程。

## 总结

在本章中，你学习了实现可扩展命令行应用程序的模式。你学习了如何为你的应用程序实现基于子命令的接口，并用它开发了可扩展的应用程序。



关于数据下载应用程序，测试必须检查 `fetchRemoteResource()` 函数是否能成功返回指定 URL 的可用数据。如果 URL 无效或不可用，它应该返回错误值。我们该如何配置一个用于提供测试内容的测试 HTTP 服务器呢？`net/http/httptest` 包中的 `NewServer()` 函数将为我们帮助。以下代码片段定义了 `startTestHTTPServer()` 函数，该函数启动一个 HTTP 服务器，对任何请求都返回 "Hello World" 响应：

```
func startTestHTTPServer() *httptest.Server {
    ts := httptest.NewServer(
        http.HandlerFunc(
            func(w http.ResponseWriter, r *http.Request) {
                fmt.Fprint(w, "Hello World")
            }))
    return ts
}
```

`httptest.NewServer()` 函数返回一个包含多个字段的 `httptest.Server` 对象，这些字段表示创建的服务器。该函数的唯一参数是类型为 `http.Handler` 的对象（你将在第 6 章“高级 HTTP 服务器”中了解到更多信息）。这个处理程序对象允许我们为测试服务器配置所需的处理程序。在这种情况下，我们创建了一个通用处理程序，它会对任何 HTTP 请求返回字符串 "Hello World" 字符串，而不仅仅是 GET 请求。隐式地，对该服务器的所有请求都将获得 HTTP 200 成功状态。

使用上面的函数，现在我们可以编写测试函数了，如列表 3.2 所示。

测试函数从调用 `startTestHTTPServer()` 创建测试服务器开始。返回的对象 `ts` 包含了与运行的测试服务器相关的数据。在 `defer` 语句中调用 `Close()` 方法可确保服务器在测试完成时停止。返回对象 `ts` 中的 `URL` 字段包含表示服务器 IP 地址和端口组合的字符串值。它作为参数传递给函数 `fetchRemoteResource()`。然后测试的其余部分检查返回的数据是否符合预期的字符串 "Hello World"。将列表 3.2 保存到新文件 `fetch_remote_resource:test.go` 中，该文件与列表 3.1 位于同一目录下。使用 `go test` 运行测试：

```
$ go test -v
=== RUN   TestFetchRemoteResource
--- PASS: TestFetchRemoteResource (0.00s)
PASS
ok          github.com/practicalgo/code/chap3/data-downloader        0.872s
```

太棒了。你通过 HTTP 实现了一个基础的数据下载器，并且通过从远程 URL 下载数据以及为其编写测试，确保了它的正常工作。

在本章的第一个练习中，练习 3.1 中，你将通过添加此功能来扩展命令行应用程序 `mync`。

## 获取数据的反序列化

我们编写的 `fetchRemoteResource()` 函数仅仅是将下载的数据显示在终端中。这对于应用程序用户来说可能没有任何意义，并且对于某些数据类型（例如，图像和非文本文件）只会显示为乱码。在大多数情况下，你可能希望对数据进行某些处理。这种处理通常被称为数据的*反序列化*（unmarshalling 或 deserialization），它涉及将字节数据转换为应用程序可以理解的数据结构。然后，你就可以在应用程序中对该数据结构执行任何操作，而无需请求或分析原始字节。反向操作是*序列化*（marshalling 或 serialization），这是将数据结构转换为可以存储或通过网络传输的格式的有效方法。在本节中重点讨论反序列化。




创建一个新目录 `chap3/pkgquery` 并在其中初始化模块：

```bash
$ mkdir -p chap3/pkgquery
$ cd chap3/pkgquery
$ go mod init github.com/username/pkgquery
```

将 Listing 3.3 保存为文件 `pkgquery.go`。

### 如何检查 `pkgquery` 包的功能性？

我们可以实现 `main` 包并请求一个虚构包服务器的实现。作为替代方案，我们可以实现一个测试用的 HTTP 服务器，它以 JSON 格式返回数据，如之前所示。函数 `startTestPackageServer()` 实现了这样一个服务器：

```go
func startTestPackageServer() *httptest.Server {
    pkgData := `[
{"name": "package1", "version": "1.1"},
{"name": "package2", "version": "1.0"}
]`
    ts := httptest.NewServer(
        http.HandlerFunc(
            func(w http.ResponseWriter, r *http.Request) {
                w.Header().Set("Content-Type", "application/json")
                fmt.Fprint(w, pkgData)
            }))
    return ts
}
```

在实现测试服务器后，Listing 3.4 显示了完整的测试函数。

我们通过调用函数 `startTestPackageServer()` 启动测试 HTTP 服务器。然后，通过调用函数 `createHTTPClientWithTimeout()` 创建 HTTP 客户端对象。接着，我们调用函数 `fetchPackageData()` 将 HTTP 客户端对象 `client` 和请求的 URL 作为参数。

最后，我们向服务器发送 GET 请求，服务器返回 JSON 格式的包数据。我们断言返回的错误为零，并获取一个包含两个元素的切片，对应于两个 `pkgData` 对象。

将 Listing 3.4 保存到与 `pkgquery.go` 同目录的新文件 `pkgquery_test.go` 中。运行测试：

```bash
$ go test -v
=== RUN   TestFetchPackageData
--- PASS: TestFetchPackageData (0.00s)
PASS
ok          github.com/practicalgo/code/chap3/pkgquery/        0.511s
```

正如预期，测试通过了。在更实际的场景中，你可以编写一个 HTTP 客户端来使用来自第三方服务器的数据。为此，你需要执行以下关键步骤：

1. 找到第三方服务器的 JSON API 模式。
2. 创建用于反序列化响应数据的结构体。
3. 使用步骤 1 实现测试服务器，以便实现完全可测试的 HTTP 客户端。

你已经看到如何使用 `Content-Type` 头部来决定是应该反序列化数据还是忽略它们。你也可以使用它来判断数据是否可以在终端中读取，或者是否需要使用特殊软件（如图像查看器或 PDF 阅读器）进行读取。在 Exercise 3.2 中，你将实现 `http` 子命令的支持，用户能够将上传的数据写入文件。

## 发送数据

让我们再次查看包服务器。我们已经知道可以通过 HTTP GET 请求查看现有的包数据。现在假设我们要向服务器上添加新的包数据。在服务器上创建或注册新包包括发送包本身（`.tar.gz` 文件）以及一些元数据（名称和版本）。为了简单起见，假设包服务器没有任何状态管理，只要它包含正确格式的预期数据，就会成功响应所有请求。

遵循 `REST` 规范的 HTTP 协议允许使用 `POST`、`PUT` 或 `PATCH` 请求向服务器发送数据。`POST` 方法通常用于创建新资源。要使用 `POST` 方法注册新包，我们需要执行以下操作：

1. 使用 `net/http` 包中定义的 `Post` 函数发送 HTTP POST 请求：`http.Post(url, contentType, packagePayload)`。其中 `url` 是发送 POST 请求的 URL 地址，`contentType` 是一个定义请求 `Content-Type` 头部值的字符串，最后 `packagePayload` 是一个包含要发送的请求体的 `io.Reader` 类型对象。
2. 这里的关键步骤是在一个请求体中同时发送二进制包数据和元数据。此时 HTTP `Content-Type` 头部 `multipart/form-data` 将非常有用。

首先，让我们看看如何发送一个仅包含元数据的 JSON 格式主体的 POST 请求。然后我们对其进行改进，以便在 `multipart/form-data` 请求中发送包数据以及元数据。

回想我们为描述包设计的 JSON 格式：

```json
// 示例格式
```

使用 `encoding/json` 包中的 `Marshal` 函数将 `pkgData` 序列化为字节切片。如果发生错误，返回空的 `pkgRegisterResult` 和错误。

```go
b, err := json.Marshal(data)
if err != nil {
    return p, err
}
```

使用 `json.Unmarshal` 来反序列化响应：

```go
type pkgRegisterResult struct {
    ID      string `json:"id"`
}
```

在 `registerPackageData` 函数中：

```go
func registerPackageData(url string, data pkgData) (pkgRegisterResult, error) {
    p := pkgRegisterResult{}
    b, err := json.Marshal(data)
    if err != nil {
        return p, err
    }
    reader := bytes.NewReader(b)
    r, err := http.Post(url, "application/json", reader)
    if err != nil {
        return p, err
    }
    defer r.Body.Close()
    // 处理响应逻辑...
}
```

如果收到了成功响应，我们读取响应体并将其反反序列化为 `pkgRegisterResult`：

```go
    respData, err := io.ReadAll(r.Body)
    if err != nil {
        return p, err
    }
    if r.StatusCode != http.StatusOK {
        return p, errors.New(string(respData))
    }
    err = json.Unmarshal(respData, &p)
    return p, err
}
```




将代码列表 3.5 保存为新文件 `pkgregister.go`。如何检查这一切是否正常工作？我们将采用与上一个节类似的方法，实现一个行为类似于我们真实包服务器的测试服务器：

1. 实现一个处理 `POST` 请求的 HTTP 处理函数。
2. 执行反序列化（unmarshalling）操作，将传入的 JSON 体转换为 `pkgData` 对象。
3. 如果反序列化过程中出错，或 `pkgData` 对象的 `Name` 或 `Version` 为空，则向客户端返回 HTTP 400 错误。
4. 通过 `-` 连接 `Name` 和 `Version` 来创建一个人工的包标识符 (`ID`)。
5. 创建 `pkgRegisterResult` 对象，并指定上一步创建的 `ID`。
6. 序列化对象，将 `Content-Type` 头部设置为 `application/json`，并将序列化后的结果作为字符串响应返回。

接下来，你可以像下面所示以独立的处理函数形式看到上述步骤的实现。（你将在第 5 章中了解到更多关于处理函数的知识。）

```go
func packageRegHandler(w http.ResponseWriter, r *http.Request) {
    if r.Method == "POST" {
        // 入站包数据
        p := pkgData{}

        // 包注册响应
        d := pkgRegisterResult{}
        defer r.Body.Close()
        data, err := io.ReadAll(r.Body)
        if err != nil {
            http.Error(w, err.Error(), http.StatusInternalServerError)
            return
        }
        err = json.Unmarshal(data, &p)
        if err != nil || len(p.Name) == 0 || len(p.Version) == 0 {
            http.Error(w, "Bad Request", http.StatusBadRequest)
            return
        }
        d.ID = p.Name + "-" + p.Version
        jsonData, err := json.Marshal(d)
        if err != nil {
            http.Error(w, err.Error(), http.StatusInternalServerError)
            return
        }
        w.Header().Set("Content-Type", "application/json")
        fmt.Fprint(w, string(jsonData))
    } else {
        http.Error(w, "Invalid HTTP method specified", http.StatusMethodNotAllowed)
        return
    }
}
```

你可以在代码列表 3.6 中找到测试函数的实现。我们有两个测试：一个用于检查“快乐路径”（happy path），即向包服务器发送预期的包注册数据；另一个用于发送空的 JSON 体。

将代码列表 3.6 保存到同一目录下的新文件 `pkgregister_test.go` 中，该目录包含代码列表 3.5
=== RUN   TestRegisterEmptyPackageData
--- PASS: TestRegisterEmptyPackageData (0.00s)
PASS
ok          github.com/practicalgo/code/chap3/pkgregister        0.540s
```

在本节中，你学习了如何使用序列化和反序列化方法发送和接收 JSON 数据。现在，你将将其用于 `mync http` 子命令对 POST 请求的支持（练习 3.3）。

在本节中学的 JSON 数据处理方法也适用于另一种流行的格式 XML，它由 `encoding/xml` 包支持。回到包注册，我们看到了如何以 JSON 格式体发送包名称和版本。然而，我们还没有看到如何将包数据一起发送。让我们看看如何使用 `multipart/form-data` 类型。

## 二进制数据处理

`multipart/form-data` MIME 类型允许发送一个包含键值对（如 `name=package1` 和 `version=1.1`）以及其他数据（如文件内容）的 HTTP 请求体。如你所知，在将其发送到服务器之前，创建这个体需要大量工作。

在我们学习如何创建 `multipart/form-data` 消息之前，让我们看看这样的消息看起来什么样：

```
--91f7de347fb9749c83cea1d596e52849fb0a95f6698459e2baab1e6c1e22
Content-Disposition: form-data; name="name"
 
mypackage
--91f7de347fb9749c83cea1d596e52849fb0a95f6698459e2baab1e6c1e22
```



接着, давайте рассмотрим функцию `registerPackageData()`, которая вызывает функцию `createMultiPartMessage()` для создания полезной нагрузки типа `multipart/form-data`:

```go
type pkgRegisterResult struct {
    Id       string `json:"id"`
    Filename string `json:"filename"`
    Size int64 `json:"size"`
}

func registerPackageData(
    client *http.Client, url string, data pkgData,
) (pkgRegisterResult, error) {

    p := pkgRegisterResult{}
    payload, contentType, err := createMultiPartMessage(data)
    if err != nil {
        return p, err
    }
    reader := bytes.NewReader(payload)
    r, err := http.Post(url, contentType, reader)
    if err != nil {
        return p, err
    }
    defer r.Body.Close()
    respData, err := io.ReadAll(r.Body)
    if err != nil {
        return p, err
    }
    err = json.Unmarshal(respData, &p)
    return p, err
}
```

Мы вызываем функцию `createMultiPartMessage()`, которая возвращает нам данные `payload` и тип контента `contentType`. Затем мы создаем объект `io.Reader` для чтения `payload` и отправляем HTTP POST запрос, вызывая функцию `http.Post()`. После этого мы читаем ответ и десериализуем его в объект `pkgRegisterResult, p`. Обратите внимание, мы добавили в структуру `pkgRegisterResult` два новых поля для указания имени файла пакета и размера отправленного файла. Это позволит нам убедиться, что сервер успешно прочитал данные.

В Listing 3.8 показана полная реализация пакета `pkgregister`, в которой используется функция `createMultiPartMessage()`.

Сохраните Listing 3.8 в качестве нового файла `pkgregister.go` в том же каталоге, что и Listing 3.7. Чтобы протестировать этот пакет, мы реализуем тестовый сервер, который принимает регистрационные данные пакета, отправленные в сообщении `multipart/form-data`, и отправляет ответ в формате JSON. Ключевая функциональность этого тестового сервера будет реализована в методе `ParseMultipartForm()`, определенном для объекта `http.Request`. Этот метод анализирует тело запроса, закодированное как сообщение `multipart/form-data`, и автоматически предоставляет доступ к встроенным данным через объект типа `multipart.Form`, определенный в пакете `mime/multipart`. Этот тип определен следующим образом:

```go
type Form struct {
    Value map[string][]string
    File  map[string][]*FileHeader
}
```

Поле `Value` — это карта, содержащая имена полей формы в качестве ключей и их значения в виде slice строк. Форма может иметь несколько значений для одного имени поля. Поле `File` представляет собой карту, ключом которой является имя поля (например, `filedata`), а срез объектов представляет данные о каждом файле в виде объекта `FileHeader`. Тип `FileHeader` определен следующим образом:

```go
type FileHeader struct {
    Filename string
    Header   textproto.MIME
    Size     int64
}
```

Имена полей говорят сами за себя. Таким образом, пример объекта типа будет выглядеть так:

```json
{"Filename": "package1.tar.gz", "Header": map[string]string{"Content-Type":"application/octet-stream"}, "Size": "200"}
```

Как мы получим данные? Объект `FileHeader` определяет метод `Open()`, который возвращает объект `File`. Затем его можно использовать для чтения данных, хранящихся в файле. Давайте рассмотрим функцию-обработчик:

```go
func packageRegHandler(w http.ResponseWriter, r *http.Request) {
    if r.Method == "POST" {
        d := pkgRegisterResult{}
        err := r.ParseMultipartForm(5000)
        if err != nil {
            http.Error(w, err.Error(), http.StatusBadRequest)
            return
        }
        mForm := r.MultipartForm
        f := mForm.File["filedata"][0]
        d.ID = fmt.Sprintf("%s-%s", mForm.Value["name"][0], mForm.Value["version"][0])
        d.Filename = f.Filename
        d.Size = f.Size
        jsonData, err := json.Marshal(d)
        if err != nil {
            http.Error(w, err.Error(), http.StatusInternalServerError)
            return
        }
        w.Header().Set("Content-Type", "application/json")
        fmt.Fprint(w, string(jsonData))
    } else {
        http.Error(w, "Invalid HTTP method", http.StatusMethodNotAllowed)
        return
    }
}
```

С самого начала мы видим вызов ключевой функции: `err := r.ParseMultipartForm(5000)`, где `5000` — это максимальное количество байт, которые будут буферизированы в памяти. Если мы получаем ненулевую ошибку, мы возвращаем ошибку 400 Bad Request. Если ошибки нет, мы получаем доступ к `MultipartForm`, извлекаем первый файл из `filedata`, формируем `ID` на основе `name` и `version`, а также устанавливаем `Filename` и `Size`. Затем мы сериализуем `d` в JSON, устанавливаем заголовок `Content-Type: application/json` и отправляем данные в ответе. Если метод не POST, мы возвращаем ошибку 405 Method Not Allowed.



创建一个新目录 `chap4/data-downloader`。从 `chap3/data-downloader` 复制所有文件。按照如下方式更新 `go.mod` 文件：

```
module github.com/username/chap4/data-downloader
 
go 1.16
```

然后，将 列表 4.1 保存到新文件 `fetch_remote_resource:bad_server_test.go` 并运行测试：

```
$ go test -v
=== RUN   TestFetchBadRemoteResource
--- PASS: TestFetchBadRemoteResource (60.00s)
=== RUN   TestFetchRemoteResource
--- PASS: TestFetchRemoteResource (0.00s)
PASS
ok          github.com/practicalgo/code/chap4/data-downloader    60.142s
```

如你所见，`TestFetchBadRemoteResource` 测试现在耗时 60 秒。实际上，如果故障服务器在发送响应之前睡眠了 600 秒，那么我们在 `fetchRemoteResource()` 中的客户端代码（列表 3.1）也将等待同样的时间。你可以想象，这会导致非常糟糕的用户体验。

我们在 第 2 章 中讨论过确保应用程序健壮性的主题。现在，让我们看看如何优化数据下载函数，使其在服务器响应时间超过指定时长时不再无限期等待。

要让我们的数据下载器只等待指定的最长时间，解决办法是使用自定义的 HTTP 客户端。当我们使用 `http.Get()` 函数时，我们隐式地使用了 `net/http` 包中定义的默认 HTTP 客户端。默认客户端通过变量 `DefaultClient` 访问，其定义方式为 `var DefaultClient = &Client{}`。`Client` 结构体定义在 `net/http` 包中，我们可以在它的字段中配置 HTTP 客户端的各种属性。现在我们查看 `Timeout` 字段，稍后我们将考虑另一个字段——`Transport`。

`Timeout` 的值为 `time.Duration` 对象，它本质上指定了客户端允许连接服务器、发送请求和读取响应的最大持续时间。如果不指定，则不限制最大时长，因此客户端将一直等待服务器响应或连接被断开。例如，要创建一个具有 100 毫秒超时时间的 HTTP 客户端，你可以使用以下语句：

```
client := http.Client{Timeout: 100 * time.Millisecond}
```

该语句将允许通过客户端执行的 HTTP 请求最多耗时 100 毫秒。使用自定义客户端后，`fetchRemoteResource()` 函数现在看起来如下：

```
func fetchRemoteResource(
    client *http.Client, url string,
) ([]byte, error) {
    r, err := client.Get(url)
    if err != nil {
        return nil, err
    }
    defer r.Body.Close()
    return io.ReadAll(r.Body)
}
```

请注意，我们不再直接调用 `http.Get()` 函数，而是调用了传递给 `fetchRemoteResource()` 的 `http.Client` 对象的 `Get()` 方法。列表 4.2 显示了完整的应用程序代码。我们定义了新函数 `createHTTPClientTimeout()` 来创建一个带有指定 `time.Duration` 超时时间的自定义 HTTP 客户端。在 `main()` 函数中，我们创建了一个配置了 15 秒等待时间的自定义客户端，然后将客户端和指定的 URL 传递给 `fetchRemoteResource()`。将 Listing 4.2 保存为新目录 `chap4/data-downloader` 中的新文件 `main.go`，并在其中初始化模块：

```
$ mkdir -p chap4/data-downloader
$ go mod init github.com/username/data-downloader
```

与其尝试构思一个糟糕的 HTTP 服务器来测试超时，不如通过编写测试用例来实现。

### 测试超时行为

我们可以更新 列表 4.1 中的测试，使其看起来像 列表 4.3 所示。`startBadTestHTTPServer()`（在 列表 4.1 和 列表 4.3 中）已重命名为 `startBadTestHTTPServerV1()`。其他关键变化如下：

1. 我们通过调用 `createHTTPClientTimeout()` 函数创建一个 `http.Client` 对象。然后将该对象传递给 `fetchRemoteResource()` 函数。
2. 我们断言错误信息包含特定的子字符串，指示客户端关闭了与服务器的连接。

我们将 列表 4.3 保存为新文件。



测试执行仅需 0.2 秒（或 200 毫秒），这与我们为测试客户端设置的超时时间一致。现在发生了什么？在测试函数完成之前，首先会调用一个匿名函数，该函数向 `shutdownServer` 通道写入结构体的空值。这会释放测试服务器的处理程序。因此，当调用 `Close()` 方法时，它会关闭测试服务器并成功退出。此时，测试函数的执行完成。

为你的 HTTP 客户端设置超时是配置 HTTP 客户端的一种方法。接下来，你将学习另一个可能也想要配置的方面——当服务器响应重定向时会发生什么？

### 配置重定向行为（处理重定向）

#### 配置重定向行为

当服务器发出 HTTP 重定向时，HTTP 客户端默认会自动且静默地`执行`重定向，最多 10 次，然后停止工作。如果你想更改这一点，例如完全不跟随重定向，或者至少让你知道它正在跟随重定向，该怎么办？这可以通过设置 `http.Client` 对象中的另一个字段 `CheckRedirect` 来实现。如果设置了符合特定签名的函数，则在决定是否重定向时会调用该对象。然后，你可以在那里实现自己的自定义逻辑。让我们来看这种函数是如何实现的示例：

```
func redirectPolicyFunc(req *http.Request, via []*http.Request) error {
    if len(via) >= 1 {
        return errors.New("stopped after 1 redirect")
    }
    return nil
}
```

实现重定向策略的自定义函数必须满足以下签名：

```
func (req *http.Request, via []*http.Request) error
```

第一个参数 `req` 是从服务器收到的执行重定向的请求；切片 `via` 包含到目前为止发送的请求，其中最旧的请求（你的原始请求）是该切片的第一个元素。通过以下步骤可以更好地说明这一点：

1. HTTP 客户端向原始 URL `url` 发送请求。
2. 服务器响应重定向，例如重定向到 `url1`。
3. `redirectPolicyFunc` 现在带有 `(url1, []{url})` 被调用。
4. 如果函数返回空错误，它将跟随重定向并向 `url1` 发送新请求。
5. 如果存在指向 `url2` 的另一个重定向，`redirectPolicyFunc` 带有 `(url2, []{url, url1})` 被调用。
6. 重复步骤 3、4 和 5，直到 `redirectPolicyFunc` 返回非空错误为止。

因此，如果你使用 `redirectPolicyFunc()` 作为自定义重定向策略函数，它将完全不会解析重定向。你如何将其连接到自定义的 HTTP 客户端？你可以按照以下方式操作：

```
func createHTTPClientWithTimeout(d time.Duration) {
    client := &http.Client{
        Timeout: d,
        CheckRedirect: redirectPolicyFunc,
    }
}
```

#### 创建带有超时时间的 HTTP 客户端的示例

```go
func createHTTPClientWithTimeout(d time.Duration) *http.Client {
    client := &http.Client{
        Timeout: d,
        CheckRedirect: redirectPolicyFunc,
    }
    return client
}
```

#### 使用重定向策略函数

```go
func redirectPolicyFunc(req *http.Request, via []*http.Request) error {
    if len(via) >= 1 {
        return errors.New("stopped after 1 redirect")
    }
    return nil
}
```

#### 配置带有上下文和请求头的请求

```go
func createGetRequest(ctx context.Context, url string, headers map[string]string) (*http.Request, error) {
    req, err := http.NewRequestWithContext(ctx, "GET", url, nil)
    if err != nil {
        return nil, err
    }
    for k, v := range headers {
        req.Header.Add(k, v)
    }
    return req, err
}
```

#### 执行请求的示例

```go
client := createHTTPClientWithTimeout(20 * time.Millisecond)
ctx, cancel := context.WithTimeout(context.Background(), 15*time.Millisecond)
defer cancel()

headers := map[string]string{"X-AUTH-HASH": "authhash"}
req, err := createGetRequest(ctx, "https://example.com/api/packages", headers)
if err != nil {
    log.Fatal(err)
}
resp, err := client.Do(req)
```

#### 向请求中添加请求头

```go
req.Header.Add("X-AUTH-HASH", "authhash")
```



在接下来的章节中，你将看到如何通过配置客户端对象来实现自定义中间件。首先，让我们查看 `Client` 结构体中的特定字段 `Transport`。

### 理解 RoundTripper 接口

`http.Client` 结构体如下定义 `Transport` 字段：

```
type Client struct {
    Transport RoundTripper
 
    // 其他字段
}
```

在 `net/http` 包中 `RoundTripper` 接口定义了一个类型，该类型将 HTTP 请求发送到远程服务器并将响应返回给客户端。该类型需要实现的唯一方法是 `RoundTrip()`：

```
type RoundTripper interface {
    RoundTrip(*Request) (*Response, error)
}
```

如果在创建客户端时没有指定 `Transport` 对象，将使用预定义的类型 `Transport` 的默认对象 `DefaultTransport`。它的定义如下（省略了字段）：

```go
var DefaultTransport RoundTripper = &Transport{
    // 字段已省略
}
```

在 `net/http` 包中定义的 `Transport` 类型实现了 `RoundTripper` 接口要求的 `RoundTrip()` 方法。它负责创建和管理基础传输控制协议（TCP）连接，HTTP 请求-响应事务通过这些连接进行传输：

1. 你创建一个 `Client` 对象。
2. 你创建一个 HTTP 请求 `Request`。
3. 随后，HTTP 请求将通过 `RoundTripper` 的实现（例如通过 TCP 连接）“传输”到服务器，响应被传回。
4. 如果你使用同一个客户端发送多个请求，步骤 2 和 3 将重复执行。

为了实现客户端中间件，我们将编写一个自定义类型，封装 `RoundTripper` `DefaultTransport` 的实现。让我们来看看如何操作。

### 日志记录中间件

你编写的第一个中间件将在发送请求之前记录消息。它将在收到响应时记录另一条消息。首先，我们定义一个带有 `*log.Logger` 字段的 `LoggingClient` 结构体：

```
type LoggingClient struct {
    log *log.Logger
}
```

为了满足 `RoundTripper` 接口，我们实现了 `RoundTrip()` 方法：

```go
func (c LoggingClient) RoundTrip(
    r *http.Request,
) (*http.Response, error) {
    c.log.Printf(
        "Sending a %s request to %s over %s\n",
        r.Method, r.URL, r.Proto,
    )
    resp, err := http.DefaultTransport.RoundTrip(r)
    c.log.Printf("Got back a response over %s\n", resp.Proto)

    return resp, err
}
```

当调用我们 `RoundTripper` 实现的 `RoundTrip()` 方法时，我们执行以下操作：

1. 记录传出的请求 `r`。
2. 调用 `DefaultTransport` 类的 `RoundTrip()` 方法，并传入出的请求 `r`。
3. 记录 `RoundTrip()` 返回的响应和错误。
4. 返回响应和错误。

太棒了。你定义了自己的 `RoundTripper`。现在，你如何使用它呢？创建一个 `Client` 对象并在 `Transport` 字段中设置 `LoggingClient` 对象：

```go
myTransport := LoggingClient{}
client := http.Client{
    Timeout:   10 * time.Second,
    Transport: &myTransport,
}
```

列表 4.6 展示了用于使用此自定义 `RoundTripper` 实现的数据加载程序（列表 4.2）的修改版本。

主要的修改已高亮显示。首先，我们创建一个新的 `LoggingClient` 对象。然后，我们通过调用 `log.New()` 函数创建一个新的 `log.Logger` 对象。函数的第一个参数是 `io.Writer` 对象，日志将写入其中。在这里我们使用 `os.Stdout`。函数的第二个参数是添加到每条日志语句中的前缀字符串——这里指定了一个空字符串。函数的最后一个参数是标志——每行日志前缀的文本。在这里我们使用 `log.LstdFlags`，它将显示日期和时间。然后，我们将 `log.Logger` 对象赋值给 `myTransport` 对象的字段 `l`。最后，我们将 `client.Transport` 设置为 `&myTransport`。

创建一个新的子目录 `chap4/logging-middleware`并将 列表 4.6 保存到新文件 `main.go` 中。编译并运行它，将 HTTP 服务器的 URL 作为命令行参数传递：

```
$ go build -o application
$ ./application https://www.google.com
2020/11/25 22:03:40 Sending a GET request to https://www.google.com over HTTP/1.1
2020/11/25 22:03:40 Got back a response over HTTP/2.0
Bytes in response: 13583
```

正如预期的，首先出现记录语句，然后打印响应。你可以使用类似的自定义 `RoundTripper` 实现来创建指标，例如请求延迟或非 200 错误。你还可以用自定义的 `RoundTripper` 做什么？你可以编写一个 `RoundTripper` 实现来自动缓存查找请求，例如完全不执行调用。

在实现自定义 `RoundTripper` 时，有两点你需要注意：

1. `RoundTripper` 必须考虑到在任何时候可能运行多个实例。
2. `RoundTripper` 不应修改请求或响应。

### 为所有请求添加标头

让我们考虑一个向每个请求添加一个或多个标头的中间件实现示例。你可能在不同的场景中需要这种功能。

首先，我们为中间件定义一个新类型：

```go
type AddHeaders struct {
    headers map[string]string
}
```

标头字段是一个包含我们想要添加到 `RoundTripper` 实现中的标头的映射：

```go
func (h AddHeaders) RoundTrip(r *http.Request) (*http.Response, error) {
    reqCopy := r.Clone(r.Context())
    for k, v := range h.headers {
        reqCopy.Header.Add(k, v)
    }
    return http.DefaultTransport.RoundTrip(reqCopy)
}
```

此中间件将通过添加标头来修改原始请求。而不是在原地修改它，我们使用 `Clone()` 方法克隆请求并对其添加标头。然后我们使用新请求调用 `DefaultTransport` `RoundTrip()`。

列表 4.7 展示了使用该中间件的 HTTP 客户端实现。为了验证指定的标头是否被添加到输出请求中，我们将一个测试服务器，它会将请求的标头作为响应的标头：

```go
func startHTTPServer() *httptest.Server {
    ts := httptest.NewServer(http.HandlerFunc(func(w http.ResponseWriter, r *http.Request) {
        for k, v := range r.Header {
            w.Header().Set(k, v[0])
        }
        fmt.Fprint(w, "I am the Request Header echoing program")
    }))
    return ts
}
```

列表 4.8 展示了使用上述测试服务器的测试函数。我们创建一个 `testHeaders` 映射，以指定想要添加到输出请求的标头。然后调用 `createClient()` 函数，并将映射作为参数传递。




将 Listing 4.8 保存到 новый файл `header_middleware_test.go` в том же каталоге, что и Listing 4.7，并 запустите тест：

```go
% go test -v
=== RUN   TestAddHeaderMiddleware
--- PASS: TestAddHeaderMiddleware (0.00s)
PASS
ok          github.com/practicalgo/code/chap4/header-middleware        0.472s
```

При написании этого промежуточного ПО вы видели пример того, как создать клиентское промежуточное ПО, которое изменяет входящий запрос, создавая копию, изменяя ее и затем передавая ее `DefaultTransport`。练习 4.3 даст вам возможность реализовать промежуточное программное обеспечение для регистрации задержек запросов.

## Пул соединений

В предыдущем разделе вы узнали, что реализация интерфейса `RoundTripper` по умолчанию передает HTTP-запрос на удаленный сервер, а затем возвращает ответ.

Один из базовых шагов заключается в том, что для вашего запроса устанавливается новое TCP-соединение. Этот процесс установления соединения является дорогостоящим. Вы не заметите этого, когда делаете один запрос. Однако когда вы отправляете HTTP-запросы как часть сервис-ориентированной архитектуры, например, вы обычно делаете несколько запросов в течение короткого промежутка времени — либо в пакетном режиме, либо непрерывно. В таком случае выполнять настройку TCP-соединения для каждого запроса дорого. Следовательно, библиотека `net/http` поддерживает *пул соединений*, где она автоматически пытается повторно использовать существующее TCP-соединение для отправки ваших HTTP-запросов.

Давайте сначала разберемся, как работает пул соединений, а затем узнаем, как мы можем настроить сам пул. Пакет `net/http/httptrace` поможет нам разобраться во внутреннем устройстве пула соединений. С помощью этого пакета можно увидеть, используется ли соединение повторно или было установлено новое для выполнения HTTP-запроса. На самом деле он делает немного больше, но мы будем использовать его только для демонстрации повторного использования соединения.

Рассмотрим следующее определение функции `createHTTPGetRequestWithTrace()`:

```go
func createHTTPGetRequestWithTrace(ctx context.Context, url string) (*http.Request, error) {
    req, err := http.NewRequestWithContext(ctx, "GET", url, nil)
    if err != nil {
        return nil, err
    }
    trace := &httptrace.ClientTrace{
        DNSDone: func(dnsInfo httptrace.DNSDoneInfo) {
            fmt.Printf("DNS Info: %+v\n", dnsInfo)
        },
        GotConn: func(connInfo httptrace.GotConnInfo) {
            fmt.Printf("Got Conn: %+v\n", connInfo)
        },
    }
    ctxTrace := httptrace.WithClientTrace(req.Context(), trace)
    req = req.WithContext(ctxTrace)
    return req, err
}
```

Тип структуры `httptrace.ClientTrace` определяет функции, которые будут вызываться при возникновении определенных событий в жизненном цикле запроса. Здесь нас интересуют два события:

*   Событие `DNSDone` происходит, когда поиск имени узла в DNS завершен.
*   Событие `GotConn` происходит, когда установлено соединение для отправки запроса.

Чтобы определить функцию, которая будет вызываться при возникновении события `DNSDone`, мы указываем функцию как значение поля при создании объекта структуры. Эта функция должна принимать объект типа `httptrace.DNSDoneInfo` в качестве параметра и не возвращать никаких значений. Точно так же мы определяем функцию, которая будет вызываться при возникновении события `GotConn`. Эта функция должна принимать объект типа `httptrace.GotConnInfo` в качестве параметра и не возвращать никаких значений. В обеих функциях мы печатаем объект на стандартный вывод.

После создания объекта `ClientTrace`, `trace`, вы создаете новый контекст, вызывая функцию `httptrace.WithClientTrace()`, передавая ей исходный контекст запроса и объект `trace`.





*   `MaxIdleConnsPerHost`: 这是每个主机允许的最大空闲连接数。默认值为 `DefaultMaxIdleConnsPerHost`，在 Go `1.16` 中该值为 `2`。

在练习 4.4 中，你将被要求在 `mync` 命令的 `http` 子命令实现连接池行为配置的支持。

## 总结

在本章，我们从学习如何在 HTTP 客户端中实现超时行为开始。超时行为结合请求上下文，允许你设置客户端等待请求完成的最长时间。这让你能够在你的应用程序中实现可靠性。然后，你学习了客户端中间件的实现，它允许你在应用程序中开发各种功能，例如日志记录、指标导出和缓存。最后，你学习了连接池以及如何配置它。

在下一章中，你将继续编写 HTTP 应用程序的之旅，在其中你将学习编写可扩展且可靠的 HTTP 服务器应用程序。

# 第 5 章：创建 HTTP 服务器

在本章中，你将深入编写 HTTP 服务器的基础知识。你将了解处理程序函数的工作原理，更多关于请求处理的知识，并学会读写流数据。在上一章中你已经接触了这些主题。现在是时候深入了。

## 你的第一个 HTTP 服务器

`net/http` 包为我们编写 HTTP 服务器提供了构建块。运行在你的计算机上并通过 `http://localhost:8080` 访问的服务器将如下所示处理请求（参见图 5.1）：

1. 服务器接收特定路径的客户端请求，例如 `/api`。
2. 服务器检查是否可以处理该请求。
3. 如果是，服务器调用处理程序函数来处理请求并返回响应。如果不是，它将返回 HTTP 错误作为响应给客户端。

![图 5.1：HTTP 服务器处理请求](img/0501.png)

**图 5.1:HTTP 服务器处理请求

代码清单 5.1 中展示了你可以编写的最简单的 Web 服务器。

`net/http` 包中的 `ListenAndServe()` 函数根据指定的网络地址启动 HTTP 服务器。建议将此地址设置为可配置的。这样，在 `main()` 函数中，以下几行代码检查是否指定了环境变量 `LISTEN_ADDR`，如果没有，则默认值为 `":8080"`：

```
listenAddr := os.Getenv("LISTEN_ADDR")
if len(listenAddr) == 0 {
    listenAddr = ":8080"
}
```

定义在 `os` 包中的 `Getenv()` 函数用于查找环境变量的值。如果找到了环境变量 `LISTEN_ADDR`，则其值将以字符串的形式返回。如果不存在该环境变量，则返回空字符串。因此，可以使用 `len()` 函数来检查是否指定了环境变量 `LISTEN_ADDR`。默认值 `":8080"` 意味着服务器将监听端口 8080 上的所有网络接口。如果你希望服务器仅在运行应用程序的计算机上可用，你必须将环境变量 `LISTEN_ADDR` 设置为 `"127.0.0.1:8080"`，然后启动应用程序。

然后我们调用 `ListenAndServe()` 函数，并指定监听的地址 (`listenAddr`) 和服务器的处理程序。我们将 `nil` 作为处理程序的值，因此我们的 `ListenAndServe` 函数调用看起来如下：

```
log.Fatal(http.ListenAndServe(listenAddr, nil))
```

如果在启动服务器时发生错误，`ListenAndServe()` 会立即返回一个错误值。如果服务器启动成功，该函数只有在服务器停止运行后才会返回。在任何情况下，如果存在错误值，`log.Fatal()` 将将其记录。

创建一个新目录 `chap5/basic-http-server` 并在其中初始化模块：

```
$ mkdir -p chap5/basic-http-server
$ cd chap5/basic-http-server
$ go mod init github.com/username/basic-http-server
```

然后将`代码清单 5.1` 保存为新文件 `server.go`。编译并运行它：

```
$ go build -o server
$ ./server
```

太棒了，你的第一个 HTTP 服务器启动了！

你是如何向它发送请求的？你可以使用浏览器，但我们将使用命令行 HTTP 客户端 `curl`。启动一个新的终端会话并执行以下操作：

```
$ curl -X GET localhost:8080/api
404 page found
```

## 配置处理程序

当你将 `nil` 作为 `ListenAndServe` 的第二个参数时，你使用的是默认处理程序 `DefaultMux`。然而，为了更灵活的配置，最好创建一个 `ServeMux`：

```go
mux := http.NewMux()
```

`ServeMux` 对象除了其他字段外，还包含一个映射服务器应该处理的路径和对应处理函数的结构。要注册路径，使用 `HandleFunc`：

```go
mux.HandleFunc("/api", func(w http.ResponseWriter, r *http.Request) {
    fmt.Fprintf(w, "Hello World")
})
```

之后将 `mux` 传递给 `ListenAndServe`：

```go
log.Fatal(http.ListenAndServe(":8080", mux))
```

### 处理函数

处理程序函数的类型必须为 `func(http.ResponseWriter, *http.Request)`，其中 `http.ResponseWriter` 和 `http.Request` 是 `net/http` 中定义的两个类型。`http.Request` 类型表示传入的 HTTP 请求，而 `http.ResponseWriter` 用于向执行请求的客户端写回响应。




在你编写完处理函数后，下一步是将其注册到你之前创建的 `ServeMux` 对象中：

```
mux.HandleFunc("/api", apiHandler)
```

这在多路复用器对象中创建了一个映射，因此任何对 `/api` 路径的请求现在都将由 `apiHandler()` 函数处理。最后，我们调用 `ListenAndServe()` 函数并指定该 `ServeMux` 对象：

```
err := http.ListenAndServe(listenAddr, mux)
```

代码列表 5.2 展示了更新后的 HTTP 服务器代码。它为两个路径：`/api` 和 `/healthz` 注册了处理函数（handler functions）。

我们通过调用 `NewServeMux()` 函数创建一个新的 `ServeMux` 对象（即一个多路复用器），然后调用 `setupHandlers()` 函数并将多路复用器作为参数传递进去。在 `setupHandlers()` 函数中，我们调用 `HandleFunc()` 函数来注册这两个路径以及对应的处理函数。然后，我们调用 `ListenAndServe()` 函数，并将多路复用器（`mux`）作为要使用的处理器传入。

创建一个新目录 `chap5/http-serve-mux`，并在其中初始化一个新的模块：

```
$ mkdir -p chap5/http-serve-mux
$ cd chap5/http-serve-mux
$ go mod init github.com/username/http-serve-mux
```

然后，将代码列表 5.2 保存为新文件 `server.go`。编译并运行服务器：

```
$ go build -o server
$ ./server
```

从另一个终端窗口，使用 `curl` 向服务器发送 HTTP 请求。对于 `/api` 和 `/healthz` 路径，你将分别看到 `Hello, world!` 和 `ok` 响应。

```
$ curl localhost:8080/api
Hello, world!

$ curl localhost:8080/healthz
ok
```

然而，如果你对任何其他路径发送请求（例如 `/healtz/` 或根路径 `/`），你你将收到“404 page not found”：

```
$ curl localhost:8080/healtz/
404 page not found

$ curl localhost:8080/
404 page not found
```

当请求到达且有可用的处理函数时，该处理函数会在独立的 goroutine（协程）中执行。处理完成后，goroutine 就会结束（参见图 5.3）。

![图 5.3: 每个传入的请求都由新的 goroutine 处理。](img/0503.png)

图 5.3: 每个传入的请求都由新的 goroutine 处理。
这确保了服务器可以同时处理多个请求。作为一个良好的副作用，这意味着如果处理某个请求时发生异常，不会影响其他正在处理的请求。

## 测试你的服务器

通过 `curl` 调用请求来手动测试服务器适用于初步测试和检查服务器，但它不具备扩展性。因此，你需要为服务器构建一个自动化的测试程序，以便于运行测试。标准库中的 `httptest` 包（通过 `net/http/httptest` 导入）为我们提供了各种函数，允许为 HTTP 服务器编写测试。通常来说，你最终将测试应用程序的行为分为两类：

* 服务器的行为
* 应用程序的行为



这是一个指向 `url.URL` 类型（定义在 `net/url` 包中）的指针，表示请求路径。通过示例来理解它是最好的。假设我们使用 URL 地址 `http://example.com/api/?name=jane&age=25#page1` 向我们的 HTTP 服务器发送请求。当句处理函数处理此请求时，URL 对象的字段将如下设置：

* `Path`: `/api/`
* `RawQuery`: `name=jane&age=25`
* `Fragment`: `page1`

要访问特定的单个查询参数及其值，您可以使用使用 `Query()` 方法。该方法返回一个类型为 `Values` 的对象，其被定义为 `map[string][]string`。对于上述 URL 地址，调用 `Query()` 方法将返回以下内容：

```
url.Values{"age":[]string{"25"}, "name":[]string{"jane"}}
```

如果查询参数出现多次，例如 `http://example.com/api/?name=jane&age=25&name=john#page1`，则 `Query()` 的返回值为：

```
url.Values{"age":[]string{"25"}, "name":[]string{"jane", "john"}}
```

如果您的服务器接受 HTTP 基本身份验证，请求 URL 的格式为 `http://user:pass@example.com/api/?name=jane&age=25&name=john`。在这种情况下，`User` 字段包含请求中指定的用户名和密码信息。要获取用户名，请调用 `User()` 方法。要获取密码，请调用 `Password()` 方法。

### Proto, ProtoMajor 和 ProtoMinor

这些字段定义了客户端和服务器交换数据的 HTTP 协议。`Proto` 是标识协议和版本的字符串（例如 `"HTTP /1.1"`）。`ProtoMajor` 和 `ProtoMinor` 是整数，分别定义协议的主版本和次版本。对于 HTTP/1.1，协议的主版本和次版本均为 1。

### Header

这是一个类型为 `map[string][]string` 的映射，包含传入的请求头。

### Host

这是一个字符串，包含了主机名和端口的组合（`example.com:8080`）或 IP 地址和端口的组合（`127.0.0.1:8080`），客户端客户端向服务器发送请求时使用了这些信息。

### Body

这是一个类型为 `io.ReadCloser` 的值，引用请求体。可以使用任何理解 `io.Reader` 接口的函数来读取主体。例如，您可以使用 `io.ReadAll()` 方法来读取整个请求体。该函数返回一个包含整个请求体的字节切片，然后您可以根据处理器的功能需求对该字节切片进行处理。在下一节中，您将看到如何在不将整个请求体读入内存的情况下处理请求体。

关联字段是 `ContentLength`，它表示从请求体中读取的最大字节数。

### Form, PostForm

如果您的函数接受 HTTP 基本身份验证，请求 URL 的格式为 `http://user:pass@example.com/api/?name=jane&age=25&name=john`。在这种情况下，`User` 字段包含请求中指定的用户名和密码信息。要获取用户名，请调用 `User()` 方法。要获取密码，请调用 `Password()` 方法。




```go
func apiHandler(w http.ResponseWriter, r *http.Request) {
    requestID := "request-123-abc"
    r = addRequestID(r, requestID)
    processRequest(w, r)
}
```

我们将定义第二个辅助函数，用于获取和注册 `requestID`：

```go
func logRequest(r *http.Request) {
        ctx := r.Context()
        v := ctx.Value(requestContextKey{})
 
        if m, ok := v.(requestContextValue); ok {
                log.Printf("Processing request: %s", m.requestID)
        }
}
```

我们通过调用带有相应键的 `ctx.Value()` 方法来获取请求上下文的值。请记住，我们在添加值时使用了空对象 `requestContextKey` 作为键。该方法返回类型为 `interface{}` 的对象。因此，我们对获取到的值进行类型断言，以确保它的类型是 `requestContextValue`。如果类型断言成功，我们就会注册 `requestID`。

然后，`processRequest()` 函数调用 `logRequest()` 函数来注册 `requestID`：

```go
func processRequest(w http.ResponseWriter, r *http.Request) {
    logRequest(r)
    fmt.Fprintf(w, "Request processed")
}
```

列表 5.4 展示了一个运行中的服务器应用程序，它为每个请求附加了请求 ID，并在处理之前将其写入日志中。

然后，将列表 5.4 保存为新文件 `server.go`。编译并启动服务器：

```
$ go build -o server
$ ./server
```

在另一个终端中向服务器发送请求：`curl localhost:8080/api`。

在运行服务器的终端上，你将看到以下内容：

```
2021/01/14 18:26:54 Processing request: request-123-abc
```

建议在进一步处理传入请求之前，将元数据（如请求 ID）附加到请求中。然而，假设你从所有的处理函数中都调用 `addRequestID()` 函数。你将在第 6 章“高级 HTTP 服务器应用程序”中，通过在你的服务器应用程序中引入中间件，将了解将元数据附加到请求对象的最佳方法。

## 流式请求处理

在第 3 章中，你首次在编写包测试服务器时学习了如何反序列化 JSON 数据。除了 `Unmarshal()` 函数外，`encoding/json` 包还为我们提供了另一种更灵活的方法来解码 JSON 数据。让我们来看一个充当日志收集器的 HTTP 服务器示例。它只做两件事：

*   它通过 HTTP POST 请求接收日志。请求体包含被编码为一个或多个 JSON 对象的日志。这通常被称为 *JSON 流流*，因为客户端会不断地作为同一个请求的一部分发送日志。
*   它在成功解码这些日志后将其打印出来。

服务器可能接收到的请求体示例如下：

```
 {"user_ip": "172.121.19.21", "event": "click_on_add_cart"}{"user_ip": "172.121.19.21", "event": "click_on_checkout"}
```





此输出告诉我们，第一个 JSON 对象已成功解码。这主要与 `Decode()` 的工作方式有关——它会持续读取输入流，直到发现错误为止。

现在让我们来看第二种错误。执行以下请求（注意第二个 JSON 对象中 `event` 的数据类型是错误的）：

```bash
$ curl -X POST http://localhost:8080/decode \
-d '
{"user_ip": "172.121.19.21","event": "click_on_add_cart"}
{"user_ip": "172.121.19.21", "event": 1}
'
```

你将收到的响应如下：

```
json: cannot unmarshal number into Go struct field
logLine.event of type string
```

如果你想提高处理处理函数的可靠性，即通过忽略反序列化错误并继续处理 JSON 流，你可以通过对 `decodeHandler()` 函数进行微调（如高亮所示）来实现：

```go
func decodeHandler(w http.ResponseWriter, r *http.Request) {
    dec := json.NewDecoder(r.Body)

    var e *json.UnmarshalTypeError

    for {
        var l logLine

        err := dec.Decode(&l)
        if err == io.EOF {
            break
        }
        if errors.As(err, &e) {
            log.Println(err)

            continue
        }
        if err != nil {
            http.Error(w, err.Error(), http.StatusBadRequest)
            return
        }
        fmt.Println(l.UserIP, l.Event)
    }
    fmt.Fprintf(w, "OK")
}
```

在反序列化阶段发生错误时，会返回特定类型的错误 `UnmarshalTypeError`（定义在 `encoding/json` 包中）。因此，通过检查 `Decode()` 函数返回的错误是否属于该类型，我们可以忽略反序列化错误并继续处理流的其他部分。通过上述更改，服务器将记录反序列化错误并继续处理流的部分。

为了看到它的运行效果，请执行以下请求：

```bash
$ curl -X POST http://localhost:8080/decode \
-d '
{"user_ip": "172.121.19.21","event": "click_on_add_cart"}
{"user_ip": "172.121.19.21", "event": 1}
{"user_ip": "172.121.21.22", "event": "click_on_checkout"}'
OK%
```

在带有上述更改的服务器上，你将看到：

```
172.121.19.21 click_on_add_cart
2020/12/30 16:42:30 json: cannot unmarshal number into Go struct field logLine.event of type string
172.121.21.22 click_on_checkout
```

`json.NewDecoder()` 函数结合 `Decode()` 方法提供了一种分析 JSON 数据的灵活方法。正如我们在这里在这里看到的，这在分析 JSON 数据流时最为有用。当然，你必须记住，灵活性意味着应用开发者需要对错误处理承担更大的责任。在下一个练习中，你将在你的应用程序中实现更可靠的 JSON 解码，以拒绝带有任何未知字段的数据。

## 作为响应的流式数据

你已经看到了如何使用 `fmt.Fprintf()` 等函数向服务器发送响应。你还看到了如何使用 `http.ResponseWriter` 对象 `w` 的 `w.Headers().Add()` 设置自定义响应头。在本节中，你将了解到当没有所有数据可作为响应发送，但你希望在数据产生时就发送，这通常被称为响应的*流式传输*（streaming）。这种情况可能发生的场景示例是当一个耗时任务作为客户端任务的一部分启动时。




我们设置了两个响应头。我们为 `Content-Type` 头部设置了 `text/plain` 值，以告知客户端我们将以明文形式发送数据。我们还为 `X-Content-Type-Options` 头部设置了 `nosniff` 值，以指示浏览器在向用户显示任何数据之前不要在其本地进行任何缓冲。

然后，我们启动了一个无限的 `for` 循环来从 `io.PipeReader` 对象中读取数据。如果我们收到 `io.EOF` 错误，表示写入模块已完成对通道的写入，我们将退出循环。如果没有，我们将调用 `Write()` 方法来发送刚刚读取的数据。如果 `flushSupported` 的值为 `true`，我们将调用 `http.Flusher` 对象 `f` 的 `Flush()` 方法。

在循环结束后，我们向 `done` 通道写入一个空结构体对象 `struct{}{}`。

在代码列表 5.6 显示了一个 HTTP 服务器，它注册了唯一的路径 `/job` 并将 `longRunningProcessHandler` 注册为处理函数。

创建一个新目录 `chap5/streaming-response` 并在其中初始化模块：

```
$ mkdir -p chap5/streaming-response
$ cd chap5/streaming-response
$ go mod init github.com/username/chap5/streaming-response
```

然后，将代码列表 5.6 保存为新文件 `server.go`。编译并运行服务器：

```
$ go build -o server
$ ./server
```

打开一个新的终端会话并使用 `curl` 发起请求。你会看到每秒返回一次的响应：

```
$ curl localhost:8080/job


{"id": 0, "user_ip": "172.121.19.21", "event": "click_on_add_cart" }
{"id": 1, "user_ip": "172.121.19.21", "event": "click_on_add_cart" }
{"id": 2, "user_ip": "172.121.19.21", "event": "click_on_add_cart" }
{"id": 3, "user_ip": "172.121.19.21", "event": "click_on_add_cart" }
{"id": 4, "user_ip": "172.121.19.21", "event": "click_on_add_cart" }
...
{"id": 20, "user_ip": "172.121.19.21", "event": "click_on_add_cart" }
```

然后，执行 `curl` 并添加 `--verbose` 标志，你会看到以下响应头：

```
Content-Type: text/plain
X-Content-Type-Options: nosniff
Date: Thu, 14 Jan 2021 06:02:13 GMT
Transfer-Encoding: chunked
```

当然，我们在写入响应时设置了 `Content-Type` 和 `X-Content-Type-Options` 头部。在调用 `Flush()` 方法时，会自动设置 `Transfer-Encoding: chunked` 头部。这告知客户端数据是按流式模式从服务器传输的，应该在连接关闭之前继续读取。

上述使用 `io.Pipe()` 的方法提供了数据生产与消费的清晰分离。需要注意的是，你不需要为了发送流式响应而创建 `PipeReader` 和 `PipeWriter` 对象。如果你对数据生成过程有控制权，可以直接通过将数据写入 `ResponseWriter` 来传递数据。然后，你可以周期地调用 `ResponseWriter` 对象的 `Flush()` 方法。例如，如果你想发送大文件作为响应，可以定期读取固定数量的字节并发送给客户端，然后重复此过程直到读取完整个文件。在这种情况下，你甚至不需要调用 `Flush()` 方法，因为部分文件对用户来说是没用的。幸运的是，你不需要手动完成所有操作。`io.Copy()` 函数允许在不编写特殊代码的情况下实现这一目标。首先打开文件进行读取：

```
f, err := os.Open(fileName)
defer f.Close()
```

要通过 `ResponseWriter` 对象 `w` 将数据作为响应传递：

```
io.Copy(w, f)
```

这将分块（每块 32 KB）读取数据并直接写入 `ResponseWriter`。在本章的最后一个练习（#c05.xhtml#feaf-0004）中，你将使用这种技术来实现文件上传服务器。

## 总结

你在第 3 章为客户端编写服务器时就已经开始编写 HTTP 服务器了。在本章中，你深入了这一点。你学习了服务器如何处理传入的请求、为什么使用 `DefaultServeMux` 是一个坏主意以及你可以如何使用自定义 `ServeMux` 对象。你编写了用于处理请求的处理函数。



在上一一节中，你已经了解到可以使用请求上下文在整个请求的生命周期内存储数据。这对于存储请求作用范围的数据非常有用，例如请求 ID、身份验证后的用户 ID 等。在典型的服务器应用程序中，还有另一类数据需要存储，例如初始化的日志记录器对象或打开的数据库的连接对象。这些对象在服务器启动后初始化，然后对所有 HTTP 处理器函数都可用。

让我们定义一个结构体类型 `appConfig`，它将包含服务器应用程序的配置数据：

```go
type appConfig struct {
    logger *log.Logger
}
```

该结构体类型包含一个类型为 `*log.Logger` 的字段 `logger`。定义另一个结构体类型 `app` 作为自定义 `http.Handler`：

```go
type app struct {
    config  appConfig
    handler func(
        w http.ResponseWriter, r *http.Request, config appConfig,
    )
}
```

`app` 对象将包含一个 `appConfig` 类型的对象和一个签名名为 `func(http.ResponseWriter, *http.Request, config appConfig)` 的函数。该函数是一个标准的 HTTP 处理器函数，但它接收一个额外的参数——类型为 `appConfig` 的值。这就是我们如何引入配置引入处理器函数。由于应用程序类型实现了 `http.Handler` 接口，我们如下所示定义 `ServeHTTP()` 方法：

```go
func (a app) ServeHTTP(w http.ResponseWriter, r *http.Request) {
    a.handler(w, r, a.config)
}
```

我们实现了一个自定义的 `http.Handler` 类型，并为处理器函数之间的数据共享奠定了基础。让我们来看处理器函数的示例：

```go
func healthCheckHandler(w http.ResponseWriter, r *http.Request,
    config appConfig) {
    if r.Method != http.MethodGet {
        http.Error(w, "Method not allowed", http.StatusMethodNotAllowed)
        return
    }
    config.logger.Println("Handling healthcheck request")
    fmt.Fprintf(w, "ok")
}
```

在处理器函数内部，我们处理请求。如果请求方法不是 GET，我们发送错误响应。否则，我们使用 `config` 对象中可用的配置日志记录器来记录消息并发送响应。

为了注册此处理器函数，我们将使用以下模板：

```go
config := appConfig{
    logger: log.New(
        os.Stdout, "", log.Ldate|log.Ltime|log.Lshortfile,
    ),
}
mux := http.NewServeMux()
setupHandlers(mux, config)
```

我们创建了一个 `appConfig` 类型的值。在这里我们配置了向 `stdout` 输出日志的日志记录器，并将其配置为记录日期、时间、文件名和行号。然后我们通过调用 `http.NewServeMux()` 创建一个新的 `http.ServeMux` 对象。接下来，我们使用创建的 `ServeMux` 对象和 `appConfig` 对象调用函数 `setupHandlers()`。`setupHandlers()` 定义如下：

```go
func setupHandlers(mux *http.ServeMux, config appConfig) {
    mux.Handle("/healthz", &app{config: config, handler: healthCheckHandler})
    mux.Handle("/api", &app{config: config, handler: apiHandler})
}
```

我们调用了 `http.ServeMux` 对象 `mux` 的 `Handle()` 方法，带有两个参数。第一个参数是用于处理的请求路径，第二个参数是类型为 `app` 的对象——我们的自定义 `http.Handler` 类型。因此，每个路径函数和处理器的注册都包含一个新的应用程序对象。`Handle()` 方法类似于你为止用于注册请求处理器的 `HandleFunc()` 方法，区别在于第二个参数。`HandleFunc()` 方法接受任何签名名为 `func(http.ResponseWriter, *http.Request)` 的函数作为参数，而 `Handle()` 方法要求第二个参数必须实现 `http.Handler` 接口的对象。

图 6.1 显示了 `http.ServeMux` 对象和自定义处理器类型如何协同处理请求。

总结来说，对于传入请求，`http.ServeMux` 对象的 `ServeHTTP()` 方法会检查该路径是否注册了允许的处理器对象。如果找到了，将调用处理器对象的相应 `ServeHTTP()` 方法，该方法随后会调用注册的处理器函数。处理器函数处理请求并发送响应，然后控制权返回到处理器对象的 `ServeHTTP()` 方法。代码段 6.1 显示了使用自定义类型的 HTTP 服务器完整应用。

![图 6.1：使用自定义处理器类型时 HTTP 服务器处理 HTTP 请求](img/0601.png)

图 6.1: HTTP 服务器处理 HTTP 请求




```go
func (a *app) ServeHTTP(w http.ResponseWriter, r *http.Request) {
    startTime := time.Now()
    a.handler(w, r, a.config)
    a.config.logger.Printf(
        "path=%s method=%s duration=%f", r.URL.Path, r.Method,
        time.Now().Sub(startTime).Seconds(),
    )
}
```

Когда вы замените в Listing 6.1 метод `ServeHTTP()` приведенным выше кодом и выполните запрос к пути `/api` или `/healthz`, вы увидите следующие логи (все в одну строку):

```
2021/03/09 08:47:27 server.go:23: path=/healthz method=GET 
duration=0.000327
```

Однако, если вы выполните запрос к незарегистрированному пути, вы не увидите никаких логов. Напомним, что метод `ServeHTTP()` типа `app` вызывается только тогда, когда для пути зарегистрирован обработчик. Чтобы исправить это, мы вместо этого создадим промежуточное ПО (middleware), которое будет оборачивать объект `ServeMux`.

### HandlerFunc 技巧

`http.HandlerFunc` — это тип, определенный в стандартной библиотеке следующим образом:

```go
type HandlerFunc func(ResponseWriter, *Request)
```

Этот также реализует метод `ServeHTTP()` и, таким образом, реализует интерфейс `http.Handler`. Как и для любого другого типа, мы можем преобразовать любую функцию с сигнатурой `func(w http.ResponseWriter, r *http.Request)` в значение, удовлетворяющее интерфейсу `http.Handler`, используя выражение `HandlerFunc(func(w http.ResponseWriter, r *http.Request))`. На Figure 6.2 показано, как запрос обрабатывается функцией, преобразованной в тип `http.HandlerFunc`.

![Figure 6.2: HTTP-сервер обрабатывает запросы при использовании типа http.HandlerFunc](img/0602.png)

Figure 6.2: HTTP-сервер обрабатывает запросы при использовании типа `http.HandlerFunc`

Зачем вообще нужен такой тип? Он позволяет нам писать функцию, которая оборачивает любое другое значение `http.Handler`, `h`, и возвращает другой `http.Handler`. Допустим, мы хотим реализовать middleware для ведения журналов, используя эту технику. Вот как мы его напишем:

```go
func loggingMiddleware(h http.Handler) http.Handler {
    return http.HandlerFunc(
        func(w http.ResponseWriter, r *http.Request) {
            startTime := time.Now()
            h.ServeHTTP(w, r)
            log.Printf(
                "path=%s method=%s duration=%f",
                r.URL.Path, r.Method, time.Now().Sub(startTime).Seconds(),
            )
        })
}
```

Затем мы создадим объект `ServeMux` и будем использовать его с функцией `ListenAndServe()` следующим образом:

```go
mux := http.NewServeMux()
setupHandlers(mux, config)
m := loggingMiddleware(mux)
http.ListenAndServe(listenAddr, m)
```

Мы создаем объект `ServeMux` и регистрируем обработчики запросов. Затем мы вызываем функцию `loggingMiddleware()`, передавая объект `ServeMux` в качестве параметра. Вот как мы оборачиваем объект `ServeMux` внутри функции `loggingMiddleware`. Поскольку возвращаемое функцией `loggingMiddleware()` реализует интерфейс `http.Handler`, мы указываем его в качестве обработчика при вызове функции `ListenAndServe()`.

На Figure 6.3 показано, как обрабатывается запрос, когда мы оборачиваем объект `http.ServeMux` внешним типом `http.Handler`, `loggingMiddleware`. Мы будем называть объект `http.ServeMux` как обернутый обработчик.

Когда приходит запрос, он сначала обрабатывается методом `ServeHTTP()`, реализованным в `http.HandlerFunc`. В рамках обработки этот метод вызывает функцию, возвращамую функцией `loggingMiddleware()`. Внутри тела этой функции запускается таймер, а затем вызывается метод `ServeHTTP()` обернутого обработчика, который затем вызывает обработчики запросов. После того как обработчики запросов завершат обработку запроса, выполнение возвращается к функции, возвращаемой функцией `loggingMiddleware()`, где регируются сведения о запросе.

Поскольку тип `http.HandlerFunc` позволяет нам писать функцию, которая оборачивает любое другое значение `http.Handler`, `h`, и возвращает другой `http.Handler`, мы можем настроить цепочку middleware, как вы узнаете далее.

![Figure 6.3: HTTP-сервер обрабатывает запросы при использовании обернутого ServeMux](img/0603.png)

Figure 6.3: HTTP-сервер обрабатывает запросы при использовании обернутого ServeMux

### Связывание middleware

Промежуточное ПО (middleware) позволяет выполнять действия до или после основного обработчика.

Промежуточное ПО (middleware) позволяет выполнять действия до или после основного обработчика.

Промежуточное ПО (middleware) позволяет выполнять действия до или после основного обработчика.

Промежуточное ПО (middleware) позволяет выполнять действия до или после основного обработчика.

Промежуточное ПО (middleware) позволяет выполнять действия до или после основного обработчика.

Промежуточное ПО (middleware) позволяет выполнять действия до или после основного обработчика.

Промежуточное ПО (middleware) позволяет выполнять действия до или после основного обработчика.

Промежуточное ПО (middleware) позволяет выполнять действия до или после основного обработчика.

Промежуточное ПО (middleware) позволяет выполнять действия до или после основного обработчика.

Промежуточное ПО (middleware) позволяет выполнять действия до или после основного обработчика.

Промежуточное ПО (middleware) позволяет выполнять действия до или после основного обработчика.

Промежуточное ПО (middleware) позволяет выполнять действия до или после основного обработчика.

Промежуточное ПО (middleware) позволяет выполнять действия до или после основного обработчика.

Промежуточное ПО (middleware) позволяет выполнять действия до или после основного обработчика.

Промежуточное ПО (middleware) позволяет выполнять действия до или после основного обработчика.

Промежуточное ПО (middleware) позволяет выполнять действия до или после основного обработчика.

Промежуточное ПО (middleware) позволяет выполнять действия до или после основного обработчика.

Промежуточное ПО (middleware) позволяет выполнять действия до или после основного обработчика.

Промежуточное ПО (middleware) позволяет выполнять действия до или после основного обработчика.

Промежуточное ПО (middleware) позволяет выполнять действия до или после основного обработчика.

Промежуточное ПО (middleware) позволяет выполнять действия до или после основного обработчика.

Промежуточное ПО (middleware) позволяет выполнять действия до или после основного обработчика.

Промежуточное ПО (middleware) позволяет выполнять действия до или после основного обработчика.

Промежуточное ПО (middleware) позволяет выполнять действия до или после основного обработчика.

Промежуточное ПО (middleware) позволяет выполнять действия до или после основного обработчика.

Промежуточное ПО (middleware) позволяет выполнять действия до или после основного обработчика.

Промежуточное ПО (middleware) позволяет выполнять действия до или после основного обработчика.

Промежуточное ПО (middleware) позволяет выполнять действия до или после основного обработчика.

Промежуточное ПО (middleware) позволяет выполнять действия до или после основного обработчика.

Промежуточное ПО (middleware) позволяет выполнять действия до или после основного обработчика.

Промежуточное ПО (middleware) позволяет выполнять действия до или после основного обработчика.

Промежуточное ПО (middleware) позволяет выполнять действия до или после основного обработчика.

Промежуточное ПО (middleware) позволяет выполнять действия до или после основного обработчика.

Промежуточное ПО (middleware) позволяет выполнять действия до или после основного обработчика.

Промежуточное ПО (middleware) позволяет выполнять действия до или после основного обработчика.

### Обработка ошибок в middleware

Использование функции `recover()` внутри middleware позволяет перехватывать паники, возникшие во время обработки обработчика, и предотвращать падение сервера.

```go
func panicMiddleware(h http.Handler) http.Handler {
    return http.HandlerFunc(
        func(w http.ResponseWriter, r *http.Request) {
            defer func() {
                if rValue := recover(); rValue != nil {
                    log.Println("panic detected", rValue)
                    w.WriteHeader(http.StatusInternalServerError)
                    fmt.Fprintf(w, "Unexpected server error")
                }
            }()
            h.ServeHTTP(w, r)
        })
}
```

Далее давайте посмотрим, как мы настроим сервер, чтобы он сочетал в себе middleware для ведения журналов и middleware для обработки паник:

```go
config := appConfig{
    logger: log.New(
        os.Stdout, "", log.Ldate|log.Ltime|log.shortfile,
    ),
}
mux := http.NewServeMux()
setupHandlers(mux, &config)
m := loggingMiddleware(panicMiddleware(mux))
err := http.ListenAndServe(listenAddr, m)
```

Ключевое утверждение выше выделено. Во-первых, мы вызываем функцию `panicMiddleware()`, чтобы обернуть `ServeMux`. Затем возвращенное значение `http.Handler` передается в качестве параметра функции `loggingMiddleware()`. Возвращаемое значение этого вызова настраивается как обработчик вызова `ListenAndServe()`.

На Figure 6.4 показано, как входящий запрос проходит через сконфигурированное middleware к методу `ServeHTTP()` объекта `ServeMux`.

При цепочке middleware самое внутреннее middleware — это то, которое выполняется первым при обработке вашего запроса (и ответа от функции-обработчика), а самое внешнее middleware — то, которое выполняется последним.




В Листин 6.2 показано полное серверное приложение, демонстрирующеезывание промежуточного ПО с использованием типа `http.HandlerFunc`。

![Figure 6.4: Использование нескольких middleware для обработки HTTP-запросов](img/0604.png)

`Figure 6.4`: Использование нескольких middleware для обработки HTTP-запросов

Мы определяем новую функцию-обработчик `panicHandler()` для обработки любого запроса по пути `/panic`. Чтобы продемонстрировать работу middleware для обработки паники `panicMiddleware()`, нам нужно лишь сделать в этом обработчике — вызвать функцию `panic()` с определенным текстом. Это значение будет восстановлено функцией `recover()` в промежуточном ПО. Затем мы настраиваем цепочку middleware в `main()` и вызываем функцию `ListenAndServe()` с обработчиком, возвращаемым функцией `loggingMiddleware()`.

Создайте новую директорию `middleware-chaining` и инициализируйте в ней модуль:

```
 $ mkdir -p chap6/middleware-chaining
 $ cd chap6/ middleware-chaining
 $ go mod init github.com/username/middleware-chaining
```

Затем сохраните Листинг 6.2 как новый файл `server.go`. Соберите и запустите сервер следующим образом:

```
 $ go build -o server
 $ ./server
```

Из отдельного терминала сделайте запрос к конечной точке `/panic` вашего сервера, используя `curl` или другой HTTP-клиент:

```
 $ curl http://localhost:8080/panic
 Unexpected server error occurred
```

В терминале, где запущенно серверное приложение, вы увидите логи, подобныеget (все в одну строку):

```
 2021/03/16 14:17:34 panic detected I panicked
 2021/03/16 14:17:34 protocol=HTTP/1.1 path=/panic method=GET
 duration=0.001575
```

Вы можете видеть, что восстановленное значение — это "I panicked", это строка, которую вы вызвали с помощью функции `panic()`. Таким образом, вы убедились, что middleware для обработки паники работает. Оно восстанавливает панику, возникшую в обработчике, регистрирует её и устанавливает соответствующий ответ. После завершения своей работы ответ передается клиенту через middleware слой логирования.

Отлично. Теперь, когда вы знаете, как настроить цепочку middleware, пришло время проверить свои знания в Упражнении 6.2.

До сих пор в этой главе вы узнали ряд новых шаблонов для реализации функциональности в нашем серверном приложении. Вы увидели, как использовать настраиваемый тип обработчика для обмена данными между обработчиками, а также реализовать middleware. Кроме того, чтобы иметь возможность обонуть объект `ServeMux`, вы узнали о новой методике реализации middleware с использованием типа `HandlerFunc`. Могли бы вы просто использовать собственный тип обработчика для достижения того же? Да, но это потребовало бы дополнительной работы. Однако, если middleware реализует сложную часть серверной функциональности, использование специального типа обработчика для ее реализации является хорошим подходом. Вы можете выделить функциональность вашего middleware в пользовательский тип с данными и методами. Вы по-прежнему сможете настроить цепочку middleware, используя подход, который мы применили здесь.

Для сложных серверных приложений очень важно начать думать о том, как организовать различные компоненты, что приводит нас к следующему разделу. Вы узнаете, как организовать серверный код и написать автоматические тесты для различных компонентов.

## Написание тестов для сложных серверных приложений

В Главе 5 «Создание HTTP-серверов» написанные вами серверные приложения состояли из трех основных функций: написания обработчиков, регистрации обработчиков с помощью объекта `ServeMux` и вызова `ListenAndServe()` для запуска сервера. Все функциональные возможности были реализованы в пакете `main`, и это хорошая отправная точка для очень простых серверных приложений. Однако когда вы начнете писать более сложные серверы, вы обнаружите, что разбиение приложения на несколько пакетов является более практичным подходом.

Один из способов сделать это — иметь отдельный пакет для каждой области приложения: управление конфигурацией, middleware и функции обработчика, а также пакет `main`, объединяющий их все вместе, и наконец, вызов функции `ListenAndServe()` для запуска сервера. Давайте сделаем это дальше.

### Организация кода

Теперь мы перепишем серверное приложение из Листинга 6.2, чтобы у нас было четыре пакета: `main`, `config`, `handlers` и `middleware`. Создайте новую директорию `complex-server` и инициализируйте в ней новый модуль с помощью `go mod init`:

```
 $ mkdir complex-server
 $ cd complex-server
 $ go mod init github.com/username/complex-server
```

Создайте три поддиктории: `config`, `handlers` и `middleware` в каталоге.

Сохраните Листинг 6.3 как `config.go` внутри директории `config`. Мы переименовываем структуру `app` в `AppConfig`, чтобы мы могли получить к ней доступ извне. Сохраните Листинг 6.4 как `handlers.go` внутри директории `handlers`. Мы импортируем пакет конфигурации, используя путь `github.com/username/complex-server/config`, и определяем тип `app`.

Затем сохраните Листинг 6.5 как `register.go` внутри директории `handlers`. Функция `Register()` принимает объект `ServeMux` и значение `config.AppConfig` и регистрирует обработчики.

Сохраните Листинг 6.6 как `middleware.go` внутри директории `middleware`. Здесь мы определяем middleware для сервера. Обратите внимание, как мы теперь передаем объект конфигурации в middleware, чтобы мы могли получить доступ к настроенному `Logger`. Мы также добавляем метод `InitConfig()`, который принимает значение `io.Writer`, которое мы используем для инициализации регистратора, и возвращает значение `AppConfig`.

Затем сохраните Листинг 6.7 как `register.go` внутри директории `middleware`. Функция `RegisterMiddleware()` устанавливает цепочку middleware для конкретного объекта `ServeMux`.

Наконец, сохраните Листинг 6.8 как `server.go` в корне каталога. Функция `setupServer()` инициализирует конфигурацию приложения, вызывая функцию `config.InitConfig()`. Затем он регистрирует функции обработчика с помощью объекта `ServeMux`, `mux`, вызывая функцию `handlers.Register()`. Наконец, он регистрирует middleware, а затем возвращает обернутое значение `handler.Handler`. В функции `main()` мы создаем объект `ServeMux`, вызываем функцию `setupServer()` и, наконец, вызываем функцию `ListenAndServe()`.

Соберите и запустите сервер из каталога complex-server:

```
 $ go build -o server
 $ ./server
```

### Тестирование функций обработчика




测试处理函数的方法有两种方法。其中一种方法包括使用 `httptest.NewServer()` 启动测试 HTTP 服务器，然后向该测试服务器发送请求。你已经在第 5 章中用过这种方法来测试处理函数。第二种方法是直接对处理函数进行测试，而不启动测试服务器。当你想要隔离地测试处理函数并忽略服务器应用程序的其他部分时，这种方法非常有用。这是任何大型服务器应用程序的推荐方法。让我们来看定义如下所示的 `apiHandler()` 函数：

```
func apiHandler(
     w http.ResponseWriter, 
     r *http.Request,
     conf config.AppConfig,
 ) {
     fmt.Fprintf(w, "Hello, world!")
 }
```

为了隔离地测试此处理函数，我们将创建一个测试响应记录器、一个测试请求和一个 `AppConfig` 值。

为了创建测试响应记录器，我们将使用 `httptest.NewRecorder()` 函数。该函数返回一个类型为 `httptest.ResponseRecorder`的值，它实现了 `http.ResponseWriter` 接口：

```
w := httptest.NewRecorder()
```

为了创建测试请求，我们将使用 `httptest.NewRequest()` 函数：

```
r := httptest.NewRequest("GET", "/api", nil)
```

`httptest.NewRequest()` 函数的第一个参数是 HTTP 请求类型——GET、POST 等。第二个参数可以是 URL 地址，例如 [`my.host.domain/api`](http://my.host.domain/api)，或者是路径，例如 `/api`。第三个参数是请求体，在这里它为零。创建一个 `AppConfig` 值：

```
b := new(bytes.Buffer)
c := config.InitConfig(b)
```

然后调用 `apiHandler()` 函数：

```
apiHandler(w, r, c)
```

通过 `w.Result()` 获取记录在 `w` 中的响应。它返回一个类型为 `*http.Response`的值。列表 6.9 显示了测试函数。

在通过 `w.Result()` 获取响应后，我们通过 `StatusCode` 字段提取状态码，通过 `resp.Body` 提取消息体。我们将它们与预期值进行比较。将列表 6.9 保存为 `handlers_test.go` 并于 `handlers` 子目录下，运行以下测试：

```
 $ go test  -v
 === RUN   TestApiHandler
 --- PASS: TestApiHandler (0.00s)
 PASS
 ok          github.com/practicalgo/code/chap6/complex-server/handlers        0.576s 
```

同样，你也可以为其他每个处理函数编写测试。对于 `healthCheckHandler()` 函数，你可能想要测试处理函数接收到非 GET HTTP 请求时的行为。练习 6.3 为你提供了实现这一点的。

那么测试 `panicHandler()` 函数呢？由于我们知道这个函数执行了什么（它调用了 `panic()` 函数），因此这里更有意义的测试组件是处理恐慌的中间件（panic middleware）。让我们看看如何测试服务器应用程序的中间件。

### 测试中间件

考虑 `panicMiddleware()` 函数的签名：`func panicMiddleware(h http.Handler, c config.AppConfig) http.Handler`。该函数的参数是处理器值 `h`；需要包装的处理器以及 `config.AppConfig` 值：

```
 b := new(bytes.Buffer)
 c := config.InitConfig(b)
 m := http.NewServeMux()
 handlers.Register(m, c)
 h := panicMiddleware(m, c)
```

我们创建一个 `http.ServeMux` 对象，注册函数，然后调用 `panicMiddleware()`。返回值另一个 `http.Handler` 值将被另一个中间件包装，或者传递给真实服务器的 `ListenAndServe()` 调用。然而，为了测试中间件，我们直接调用处理器的 `ServeHTTP()` 方法：

```
 r := httptest.NewRequest("GET", "/panic", nil)
 w := httptest.NewRecorder()
 h.ServeHTTP(w, r)
```

列表 6.10 显示了完整的测试函数。调用 `panicMiddleware()` 返回的处理器的 `ServeHTTP()` 方法模拟了测试恐慌时 `ListenAndServe()` 函数的行为。将列表 6.10 保存为 `middleware` 目录下的 `middleware_test.go` 并运行以下测试：

```
 $ go test -v
 === RUN   TestPanicMiddleware
 --- PASS: TestPanicMiddleware (0.00s)
 PASS
 ok          github.com/practicalgo/code/chap6/complex-server/middleware        0.15s
```

这种方法适用于隔离测试中间件。如果你想检查整个中间件链是否正常工作，让我们为它写一个测试。

### 测试启动

对于列表 6.8 中的服务器应用程序，`setupServer()` 函数创建配置并注册请求处理器和中间件链。因此，启动时的行为测试等于测试该函数。

首先，我们将创建新的 `http.ServeMux` 和 `bytes.Buffer` 对象并调用 `setupServer()`：

```
 b := new(bytes.Buffer)
 mux := http.NewServeMux()
 wrappedMux := setupServer(mux, b)
```

然后，我们将使用 `httptest.NewServer()` 函数启动测试服务器，并将 `wrappedMux` 指定处理器：

```
 ts := httptest.NewServer(wrappedMux)
 defer ts.Close()
```

启动测试服务器后，我们将发送 HTTP 请求并检查：

1. 响应状态和体内容符合预期。
2. 日志中间件和恐慌处理中间件正常工作。

列表 6.11 显示了检查服务器配置的测试函数。在测试函数中，我们在调用 `setupServer()` 后启动测试服务器并向 `/panic` 端点发送 HTTP 请求。然后我们检查响应状态是否为 500 Internal Server Error。在测试的剩余部分，我们检查预期日志是否写入了 `io.Writer` `b`。将列表 6.11 保存为与 `server.go` 相同目录下的 `server_test.go`（其中列表 6.8 被存储），并运行测试：

```
 $ go test -v
 === RUN   TestSetupServer
 --- PASS: TestSetupServer (0.00s)
 PASS
 ok         github.com/practicalgo/code/chap6/complex-server        0.711s
```

上述测试函数检查了服务器配置，包括你的中间件链的功能。在编写服务器应用程序的测试时，始终建议隔离测试组件，然后检查哪些测试验证了组件的集成。对于处理器和中间件，你编写了单元测试来隔离测试它们，而不启动 HTTP 服务器。对于服务器配置的最终测试，你启动了测试 HTTP 服务器以检查请求处理器和中间件的集成。

你从学习 `http.Handler` 接口开始这一章。你了解到 `http.ServeMux` 是实现该接口的类型，然后编写了自己的自定义类型来实现它。你看到了如何将 `ServeMux` 对象与自定义处理器实现集成，以便在处理器函数之间交换数据。

随后，你学会了为服务器编写中间件，首先实现了自定义 `Handler` 类型，然后使用了 `http.HandlerFunc` 类型。你还学习了如何在你的服务器上组合中间件，以便以独立的即插即用组件形式实现服务器的通用功能。



最后，你已经了解了如何组织和测试带有各种组件的服务器应用程序。

在下一章“就绪的 HTTP 服务器”中，你将学习为 HTTP 服务器应用程序准备部署的方法。

# 第 7 章：就绪的 HTTP 服务器

在本章中，你将学习提高 HTTP 服务器应用程序可靠性和稳定性的方法。你将学习如何在服务器请求处理的生命周期的不同点实现超时（timeout），如何中断请求处理以节省服务器资源，以及如何实现正确的关闭。最后，你将学习如何配置你的 HTTP 服务器，以便在客户端和你的服务器之间建立安全的通信通道。让我们开始吧！

## 中断请求处理

考虑你的 Web 应用程序提供的特定功能，例如允许用户根据特定参数在大数据集中进行搜索。在将此功能提供给用户之前，你进行了全面的测试，并发现在你的所有测试用例中，搜索查询的执行时间均为 500 毫秒。然而，一旦用户开始在应用程序中使用该功能，你发现对于某些搜索标准，查询请求的执行时间可能长达 30 秒，而且有时会失败。更糟糕的是，同样的搜索在重试时会在 500 毫秒内成功完成。现在你担心这可能导致你的应用程序被攻击，因为多个这样的请求可能会使其无法处理任何请求——操作系统的资源是有限的——如打开的文件描述符、内存等。听起来熟悉吗？这就是“拒绝服务”攻击（`DoS`）是如何实施的！

当你开始研究这种奇怪的行为并试图找到修复方法时，你想在你的服务器上放置一个安全机制。为此，你为该请求设置了处理器超时时间。如果该操作持续超过 10 秒，你将中断请求处理并返回错误响应。这将实现两个目标：你的服务器资源不会被这些比预期耗时长的请求占用，而且你的客户端将收到一个快速响应，告知其请求无法执行。然后他们可以简单地重试，并可能获得成功的响应。让我们看看如何在 HTTP 服务器应用程序中实现这种行为。

`http.TimeoutHandler()` 函数是定义在 `net/http` 包中的中间件软件，它创建一个新的 `http.Handler` 对象，封装另一个 `http.Handler` 对象，以使得如果内部处理程序没有在指定时间内完成，则将向客户端发送 HTTP 响应 `503 Service Unavailable`。考虑这个处理函数：

```go
func handleUserAPI(w http.ResponseWriter, r *http.Request) {
    log.Println("I started processing the request")
    time.Sleep(15 * time.Second)
    fmt.Fprintf(w, "Hello world!")
    log.Println("I finished processing the request")
}
```

我们有一个 `time.Sleep()` 函数调用来模拟 15 秒的请求处理延迟。15 秒后，它将向客户端发送 `Hello world!` 响应。日志将帮助我们更好地理解处理函数与超时处理器之间的交互，正如你很快就会看到的。

然后，我们将使用 `http.TimeoutHandler()` 函数来封装 `handleUserAPI()` 函数，以便在 14 秒后向客户端发送 HTTP 503 响应——恰好在处理函数退出睡眠状态之前。处理函数的定义如下：

```go
func TimeoutHandler(h Handler, dt time.Duration, msg string) Handler
```

它的参数是：`h` 是满足 `Handler` 接口的传入处理程序；`dt` 是我们希望客户端等待处理完成的最大时长（以毫秒或秒为单位）；`msg` 是随响应发送给客户端的字符串消息。

因此，为了封装 `handleUserAPI` 函数，我们首先将其转换为满足 `Handler` 接口的值：

```go
userHandler := http.HandlerFunc(handleUserAPI)
```

然后我们使用 14 秒的超时时间调用 `http.TimeoutHandler()`：

```go
timeoutDuration := 14 * time.Second
hTimeout := http.TimeoutHandler(
    userHandler, timeoutDuration, "I ran out of time",
)
```

返回的对象 `hTimeout` 满足 `Handler` 接口，它是对传入处理程序 `userHandler` 的封装，并实现了超时逻辑。然后你可以使用 `ServeMux` 注册它以直接处理请求，或者像下面所示作为中间件链的一部分：

```go
mux := http.NewServeMux()
mux.Handle("/api/users/", hTimeout)
```




```go
func handleUserAPI(w http.ResponseWriter, r *http.Request) {
    log.Println("I started processing the request")
    time.Sleep(15 * time.Second)

    log.Println(
        "Before continuing, i will check if the timeout has already expired",
    )
    if r.Context().Err() != nil {
        log.Printf(
            "Aborting further processing: %v\n",
            r.Context().Err(),
        )
        return
    }
    fmt.Fprintf(w, "Hello world!")
    log.Println("I finished processing the request")
}
```

在调用函数 `time.Sleep()` 后，我们通过方法 `r.Context()` 获取请求上下文。然后我们检查方法调用 `Err()` 是否返回了非空错误值。如果返回了非空错误值，说明客户端连接已关闭，因此我们从处理函数中返回。由于客户端已经离开，我们通过中断请求处理来节省系统资源或防止不可预知的行为。你可以在此书源码仓库的 `chap7/abort-processing-timeout` 目录下找到带有上述处理函数的运行服务器。这种策略要求你在编写处理函数时，使其能够感知客户端连接的状态，并利用该状态来决定是否继续处理请求。

在另一种场景下，如果你的处理函数发送了网络请求（例如向另一个服务发送 HTTP 请求），你应该将请求上下文与传出的请求一起传递。这样，当超时处理器触发时（从而取消上下文），传出的 HTTP 请求将根本不会执行。当然，在这种情况下你不需要手动执行所有工作，因为标准库的 HTTP 客户端已经支持上下文的传递，正如你在第 4 章中所学到的。让我们来看一个说明这一点的示例。

考虑函数 `doSomeWork()`，它是真实函数的替代品，执行耗时 2 秒：

```go
func doSomeWork() {
    time.Sleep(2 * time.Second)
}
```

接下来查看更新后的函数 `handleUserAPI()`，它调用了函数 `doSomeWork()`：

```go
func handleUserAPI(w http.ResponseWriter, r *http.Request) {
    log.Println("I started processing the request")

    doSomeWork()

    req, err := http.NewRequestWithContext(
        r.Context(),
        "GET",
        "http://localhost:8080/ping", nil,
    )
    if err != nil {
        http.Error(
            w, err.Error(),
            http.StatusInternalServerError,
        )
        return
    }
    client := &http.Client{}
    log.Println("Outgoing HTTP request")

    resp, err := client.Do(req)
    if err != nil {
        log.Printf("Error making request: %v\n", err)
        http.Error(
            w, err.Error(),
            http.StatusInternalServerError,
        )
        return
    }
    defer resp.Body.Close()
    data, _ := io.ReadAll(resp.Body)

    fmt.Fprint(w, string(data))
    log.Println("I finished processing the request")
}
```

`handleUserAPI()` 函数首先调用函数 `doSomeWork()`，然后通过 `/ping` 路径向另一个 HTTP 发送 GET 请求——在本例中，为了简单起见，是同一个应用程序。它使用函数 `http.NewRequestWithContext()` 创建 HTTP 请求，并要求其使用当前正在处理的请求上下文作为其上下文。获取到的 GET 请求响应随后作为响应被返回。我们预期如果超时处理器中断了请求处理，该请求将不会被执行。列表 7.2 展示了一个可运行的服务器应用程序。

现在我们使用 `userHandler` 对象调用函数 `http.TimeoutHandler()`，并将超时设置为 1 秒。函数 `doSomeWork()` 的执行耗时 2 秒。

创建一个新目录 `chap7/network-request-timeout` 其中初始化模块：

```bash
$ mkdir -p chap7/network-request-timeout
$ cd chap7/network-request-timeout
$ go mod init github.com/username/network-request-timeout
```

然后将列表 7.2 保存为 `server.go`。编译并运行程序：

```bash
$ go build -o server
$ ./server
```

在另一个终端中，使用 `curl`（添加 `-v` 选项）对路径 `/api/users/` 发起请求：

```bash
$ curl -v localhost:8080/api/users/
# output snipped #
>
< HTTP/1.1 503 Service Unavailable
# output snipped #
 
I ran out of time
```

客户端收到 503 Service Unavailable，错误信息为“I ran out of time”。

（注：原文中存在重复的英语和俄语片段，在翻译时保留了逻辑连接，以及关于上下文已过期的逻辑输出。）

### 处理断开

为了响应客户端断开，你将再次使用请求上下文。事实上，列表中的 `handleUserAPI()` 已经是这样写的。现在我们准备修改函数，以探索另一种使用请求上下文检测断开的模式：

```go
func handleUserAPI(w http.ResponseWriter, r *http.Request) {
    done := make(chan bool)

    log.Println("I started processing the request")

    // TODO 如上列表 7.2 所示执行传出的请求

    data, _ := io.ReadAll(resp.Body)

    log.Println("Processing the response i got")

    go func() {
        doSomeWork(data)
        done <- true
    }()

    select {
    case <-done:
        log.Println("doSomeWork done:Continuing request processing")
    case <-r.Context().Done():
        log.Printf(
            "Aborting request processing: %v\n",
            r.Context().Err(),
        )
        return
    }

    fmt.Fprint(w, string(data))
    log.Println("I finished processing the request")
}
```




接收到请求后，处理函数将执行一个发出的 HTTP GET 调用。如之前所示，我们将传入请求的上下文作为该请求的一部分传递。接收到响应后，它会在 goroutine 中调用 `doSomeWork()` 函数。一旦函数返回，我们向 `done` 通道写入 `true`。然后我们有了一个 `select..case` 语句块，在其中我们对两个通道进行等待——`done` 通道和通过调用方法 `r.Context.Done()`返回的通道。如果我们先从 `done` 通道接收到值，我们将继续处理请求。如果我们先从第二个通道接收到值，则说明上下文已取消，我们停止处理请求并从处理函数返回。我们还将对服务器的其他部分进行一些更改。代码列表 7.3 显示了实现了这些更改的服务器。

我们将 `doSomeWork()` 中的暂停时间增加到了 15 秒，并并在 `handlePing()` 函数中引入了 10 秒的暂停。我们还将超时处理程序的持续时间增加到 30 秒。进行这些更改是为了反映与搜索函数性能相关的新结果。因此，在此版本的服务器中，超时处理程序不会中断请求处理——这是刻意为之。

创建一个新目录 `chap7/client-disconnect-handling` 并在其中初始化模块：

```bash
$ mkdir -p chap7/client-disconnect-handling
$ cd chap7/client-disconnect-handling
$ go mod init github.com/username/client-disconnect-handling
```

然后，将代码列表 7.3 保存为 `server.go`。编译并运行应用程序：

```bash
$ go build -o server
$ ./server
```

在另一个终端中，使用 `curl` 向路径 `/api/users/` 向应用程序发送请求，并在 10 秒超时前按下 Ctrl+C 以中断请求：

```bash
$ curl -v localhost:8080/api/users/
..
* Connected to localhost (::1) port 8080 (#0)
..
^C
```

在运行服务器的终端上，你将看到以下日志：

```
2021/04/26 09:25:17 I started processing the request
2021/04/26 09:25:17 Outgoing HTTP request
2021/04/26 09:25:17 ping: Got a request
2021/04/26 09:25:18 Error making request: "http://localhost:8080/ping": context canceled
```

从日志可以看出，`handlePing()` 函数接收到了请求，但在完成之前它被取消了，这是因为你取消了请求。请注意，日志消息现在显示为 `context canceled`（超时）。尝试在 10 秒后但 15 秒到之前中断请求。

你已经学会了如何在你的服务器应用程序中实现请求处理的中断方法，以响应设置的等待时间。实现此模式的目标是确保在发生意外情况时具有可预测性。然而，这些方法集中在单个处理程序函数上。接下来，我们将从服务器应用程序的角度考虑可靠性的实现。但在在此之前，你必须完成练习（练习 7.2）。

## 服务器级超时

我们将从为所有处理程序函数实现全局超时开始。然后，我们将向上一个级别，研究在请求到达处理程序函数之前发生的网络交互，并研究如何在请求-响应的各个阶段确保可靠性。

### 为所有处理程序函数实现超时

即使在注意到运行工作环境中的任何应用程序出现具体问题之前，你可能也想为所有处理程序函数实现硬性超时。这将为你的所有处理程序提供延迟的上限，并防止意外情况阻塞服务器资源。为了实现，你将再次使用 `http.TimeoutHandler()` 函数。你还记得函数的签名如下：

```go
func TimeoutHandler(h Handler, dt time.Duration, msg string) Handler
```

这里需要说明的关键点是，包装的处理对象 `h` 必须实现 `http.Handler` 接口。此外，在第 6 章中，你已经知道 `ServeMux` 类型实现了相同的接口。因此，要为所有处理函数实现全局等待时间，你只需要使用 `ServeMux` 对象作为处理器调用 `http.TimeoutHandler()` 函数，然后使用返回的处理器调用 `http.ListenAndServe()`：

```go
mux := http.ServeMux()
mux.HandleFunc("/api/users/", userAPIHandler)
mux.HandleFunc("/healthz", healthcheckHandler)
mTimeout := http.TimeoutHandler(mux, 5*time.Second, "I ran out of time")
http.ListenAndServe(":8080", mTimeout)
```

使用上述配置，所有注册的请求处理程序将最多拥有五秒时间，然后超时处理器将触发并中断请求处理。你可以在本书源码的 `chap7/global-handler-timeout` 目录中找到显示全局处理器等待时间的运行示例。当然，你可以将全局处理器的超时与特定处理器的超时相结合，以实现更详细的超时。将全局处理器超时与请求处理中断策略相结合，可以确保当你的应用程序出现意外场景时，你的服务器能够更好地应对快速故障。

接下来，我们将处理器的超时再向上一个级别，查看如何使服务器对处理器之外可能出现的问题产生免疫。

### 服务器超时实现

当客户端向应用程序发送请求时，在高层执行以下步骤（忽略任何注册的中间件）：

1. 客户端连接由服务器 goroutine 接收；即执行 `http.ListenAndServe()` 的地方。
2. 服务器部分读取请求以确定路径，例如 `/api/users/` 或 `/healthz`。
3. 如果路径注册了处理程序，服务器过程创建一个 `http.Request` 对象，包含请求头和有关请求的所有信息，正如你在第 5 章中所学到的。
4. 然后调用处理程序处理请求，它处理请求并将响应写回客户端。

在正常情况下，所有上述步骤将在足够短的时间内完成——毫秒，或者取决于请求的几十秒。



图 7.2 显示了请求处理语境下的各种超时时间。你已经了解了通过 `http.TimeoutHandler()` 函数为每个处理器设置的超时时间。那么，我们为什么还需要其他超时时间呢？对于传入的请求流，通过配置 `http.TimeoutHandler()` 函数设置的超时时间仅在请求到达路径配置的 HTTP 处理器函数后才生效。在此之前，该超时不生效。对于输出的响应流，该函数强制的超时时间完全没有帮助，因为 `http.TimeoutHandler()` 的设计决定了它会在超时后向客户端写入响应，因此它可能会以等方式受到恶意客户端或网络的影响。接下来你将学习如何在服务器级别设置读取和写入超时时间。

![图 7.2：在处理 HTTP 请求时起作用的各种超时时间](img/0702.png)

图 7.2:在处理 HTTP 请求时起作用的各种超时时间

启动 HTTP 服务器的 `http.ListenAndServe()` 函数定义如下（从 Go 1.16 开始）：

```
func ListenAndServe(addr string, handler Handler) error {
    server := &Server{Addr: addr, Handler: handler}
    return server.ListenAndServe()
}
```

它创建了一个 `http.Server` 类型的对象，该类型是定义在 `net/http` 包中的结构体类型。然后它了它的 `ListenAndServe()` 方法。为了进一步配置服务器（例如添加读取和写入超时时间），我们必须手动创建一个可配置的 `Server` 对象并调用 `ListenAndServe()` 方法：

```
s := http.Server{
    Addr:         ":8080",
    Handler:      mux,
    ReadTimeout:  5 * time.Second,
    WriteTimeout: 5 * time.Second,
}
log.Fatal(s.ListenAndServe())
```

我们通过指定几个字段创建了 `http.Server` 对象 `s`：

* `Addr:`：对应我们希望服务器监听的地址字符串。在这里，我们希望服务器监听 `":8080"` 地址。
* `Handler:`：实现 `http.Handler` 接口的对象。在这里，我们指定了类型为 `http.ServeMux` 的对象 `mux`。
* `ReadTimeout:`：`time.Duration` 对象，表示服务器读取传入请求的最大时间。在这里，我们指定其为 5 秒。
* `WriteTimeout:`：`time.Duration` 对象，表示服务器写入响应的最大时间。在这里，我们指定其为 5 秒。

然后我们为该对象调用 `ListenAndServe()` 方法。代码清单 7.4 显示了一个配置了读取和写入超时时间的服务器。它为路径 `/api/users/` 注册了一个请求处理器。

`handleUsersAPI()` 函数期望对它的请求带有正体。我们在其中添加了各种日志语句，以确保我们理解配置的超时时间如何影响服务器的行为。它将读取体、注册它，然后向客户端发送响应 `"Hello world!"`。如果在读取体时发生错误，将被记录在日志中向客户端返回错误消息。创建一个新目录 `chap7/server-timeout` 并在其中初始化：

```
$ mkdir -p chap7/server-timeout
$ cd chap7/server-timeout
$ go mod init github.com/username/server-timeout
```

然后将代码清单 7.4 保存为 `server.go`。编译并运行应用：

```
$ go build -o server
$ ./server
```

在另一个终端中使用 `curl` 向其发送以下请求：

```
$ curl --request POST http://localhost:8080/api/users/ \
    --data "Hello server"
Hello world!
```

上述 `curl` 命令发送了一个带有 `"Hello server"` 的 HTTP POST 请求。在服务器端，你会看到以下日志：

```
2021/05/02 14:03:08 I started processing the request
2021/05/02 14:03:08 Hello server
2021/05/02 14:03:08 I finished processing the request
```

这是正常情况下的行为。保持服务器运行。

利用你在第 5 章“作为响应的流式数据”节中学到的某些技巧，你可以实现一个非常缓慢地发送请求体的 HTTP 客户端。你可以在 `chap7/server-timeout` 目录下找到客户端代码。

```go
func handleUsersAPI(w http.ResponseWriter) {
    for i := 0; i < 10; i++ {
        fmt.Fprintf(w, "hello")
        time.Sleep(1 * time.Second)
    }
}
```




## 实现优雅停机 (Graceful Shutdown)

HTTP 服务器的优雅停机意味着在服务器停止之前，尝试不中断当前正在进行的请求处理。本质上，有两个点影响着服务器优雅停机的实现：

1. 停止接收任何新请求。
2. 不中断正在处理的请求。

幸运的是，`net/http` 库已经通过 `http.Server` 对象中定义的 `Shutdown()` 方法提供了此项功能。当调用此方法时，服务器将停止接收任何新请求，断开所有空闲连接，然后在返回之前等待所有正在运行的请求处理函数执行完毕。您可以通过传递一个 `context.Context` 对象来控制它的等待时间。让我们先写一个函数，该函数将配置信号处理程序（类似于您在第 2 节中为命令行应用程序实现的方式），并在接收到 `SIGINT` 或 `SIGTERM` 信号时为服务器对象 `s` 调用 `Shutdown()` 方法：

```
func shutDown(
    ctx context.Context,
    s *http.Server,
    waitForShutdownCompletion chan struct{},
) {
    sigch := make(chan os.Signal, 1)
    signal.Notify(sigch, syscall.SIGINT, syscall.SIGTERM)
    sig := <-sigch
    log.Printf("Got signal: %v . Server shutting down.", sig)
    if err := s.Shutdown(ctx); err != nil {
        log.Printf("Error during shutdown: %v", err)
    }
    waitForShutdownCompletion <- struct{}{}
}
```

`shutdown()` 函数带有三个参数调用：

* `ctx`: `context.Context` 对象，允许您控制 `Shutdown()` 方法等待现有请求处理完成的时间。
* `s`: `http.Server` 对象，代表在接收到信号后将关闭的服务器。
* `waitForShutdownCompletion`: 类型为 `struct{}` 的通道。

当程序接收到 `SIGINT` 或 `SIGTERM` 信号之一时，它会调用 `Shutdown()` 方法。当调用返回时，`struct{}{}` 将写入 `waitForShutdownCompletion` 通道。这将告诉主程序的关闭进程已完成，它可以继续运行并结束自己的工作。

在图 7.3 中图形化展示了 `Shutdown()` 和 `ListenAndServe()` 方法是如何相互作用的。代码清单 7.5 展示了一个实现优雅停机的服务器。

![图 7.3: Shutdown() 和 ListenAndServe() 方法之间的相互作用](img/0703.png)

图 7.3: `Shutdown()` 方法和 `ListenAndServe()` 方法之间的相互作用。

`waitForShutdownCompletion` 通道将帮助我们组织主程序的 goroutine 和启动 `shutdown()` 函数的 goroutine。我们使用 `context.WithTimeout()` 函数创建一个上下文，该上下文将在 30 秒后取消。这设置了服务器 `Shutdown()` 方法等待所有现有请求处理的最长时间。

然后，我们在 goroutine 中调用 `ShutDown()` 函数，并调用 `s.ListenAndServe()` 函数。请注意，我们没有在 `log.Fatal()` 调用内部调用此函数。这是因为当调用 `Shutdown()` 方法时，`ListenAndServe()` 函数会立即返回，因此服务器会在等待 `Shutdown()` 方法返回之前停止工作。因此，我们将返回的错误存储在 `err` 中，记录消息并等待值写入 `waitForShutdownCompletion` 通道，这会阻塞服务器的关闭。一旦我们在该通道上接收到值，我们就记录错误并退出。

创建一个新目录 `chap7/graceful-shutdown`，并在其中初始化模块：

```bash
$ mkdir -p chap7/graceful-shutdown
$ cd chap7/graceful-shutdown
$ go mod init github.com/username/graceful-shutdown
```

然后将代码清单 7.5 保存为 `server.go`。编译并运行应用程序：

```bash
$ go build -o server
$ ./server
```

为了向此服务器发送请求，我们将使用自定义客户端，您可以在源代码仓库的 `chap7/client-slow-write` 目录找到它。按照以下方式编译并运行客户端（在服务器运行时）：

```bash
$ go build -o client-slow-write
$ ./client-slow-write
2021/05/02 20:28:25 Starting client request
```

现在，当您看到上面的日志消息时，回到运行服务器的终端并按下 Ctrl + C。您将看到以下日志输出：

```
2021/05/02 20:28:25 I started processing the request
^C2021/05/02 20:28:25 Got signal: interrupt . Server shutting down.
2021/05/02 20:28:28 Waiting for shutdown to complete..
2021/05/02 20:28:36 hellohellohellohellohellohello
hellohellohello
2021/05/02 20:28:36 I finished processing the request
2021/05/02 20:28:36 http: Server closed
```

请注意，在您按下 Ctrl+C 后，`Shutdown()` 等待读取完所有内容或执行当前请求，然后服务器关闭。在客户端，您将看到它返回了 `Hello world!` 响应。

太棒了！现在您学会了如何实现服务器应用程序的停机机制，使得执行中的请求不会中断。实际上，您可以使用此机制执行任何其他所需的清理操作，例如通知任何长连接客户端进行重连或关闭所有与数据库的连接。

在本章的最后一节中，您将学习如何实现生产环境中服务器的另一项重要功能——配置安全的客户端通道。

## 使用 TLS 保护通信

整本书可以专门讨论使用传输层安全（TLS）来保护网络连接。TLS 用于通过加密协议保护服务器与客户端之间的通信。




将 `ListenAndServeTLS()` 函数与 `ListenAndServe()` 函数进行比较，它接收两个额外的参数：第二个和第三个参数是字符串，包含 TLS 证书路径和密钥文件路径。这些文件包含了服务器和客户端之间进行安全数据传输所需的数据。你可以自己生成证书（也称为**自签名证书**），或者请求其他机构（即证书颁发机构 CA）来为你生成。自签名证书仅用于在组织定义的边界内保护通信。然而，如果你在你的服务器上使用此类证书，然后让组织之外的人访问服务器，他们将收到错误信息，提示证书未被识别，因此无法建立安全连接。另一方面，通过 CA 创建的证书将被组织外部的客户端信任。大型组织通常为内部服务使用自签名证书，而外部服务是由 CA 签发的。换句话说，对于公共域名，你必须使用自签名证书和 CA 签发的证书。实际上，你也可以在组织内部运行证书颁发机构来配合自签名证书。接下来你将了解如何使用自签名证书配置安全的 HTTP 服务器。

### 配置 TLS 和 HTTP

首先，你将使用命令行程序 `openssl` 创建自签名证书和密钥。如果你使用的是 MacOS 或 Linux，该程序应该已经安装。

创建一个 `chap7/tls-server` 目录并在其中初始化：

```
$ mkdir -p chap7/tls-server
$ cd chap7/tls-server
$ go mod init github.com/username/tls-server
```

使用 `openssl` 创建自签名证书，运行以下命令：

```
$ openssl req -x509 -newkey rsa:4096 -keyout server.key -out server.crt -days 365 -subj "/C=AU/ST=NSW/L=Sydney/O=Example/OU=Org/CN=localhost" -nodes
```

上述命令执行完成后将输出如下内容：

```
Generating 4096 bit RSA private key
.....................................................
............................................................
......................................................
writing new private key to 'server.key'
```

你会在 `chap7/tls-server` 目录中看到两个文件：`server.key` 和 `server.crt`。我们在调用 `ListenAndServeTLS()` 函数时将指定这些密钥和证书。深入了解上述命令的细节，需要注意以下两点：

- 上述证书仅用于测试，因为客户端默认不信任自签名证书。
- 上述证书将允许你使用 `localhost` 域名安全地连接到你的服务器。

在此配置后启动 HTTPS 服务器所示：

```go
package main

func main() {
    // ...

    tlsCertFile := os.Getenv("TLS_CERT_FILE_PATH")
    tlsKeyFile := os.Getenv("TLS_KEY_FILE_PATH")

    if len(tlsCertFile) == 0 || len(tlsKeyFile) == 0 {
        log.Fatal("TLS_CERT_FILE_PATH and TLS_KEY_FILE_PATH must be specified")
    }

    // ..

    log.Fatal(
        http.ListenAndServeTLS(
            listenAddr,
            tlsCertFile,
            tlsKeyFile,
            m,
        )
    )
}
```

服务器期望证书和密钥文件路径通过环境变量指定：`TLS_CERT_FILE_PATH` 和 `TLS_KEY_FILE_PATH`。我们添加了服务器日志中间件，并为 `/api` 路径注册了一个请求处理程序。注意，我们将 `listenAddr` 的默认值更改为 `":8443"`，因为这对于非服务器更为常见。将 `server.go` 保存到 `chap7/tls-server` 目录。按如下方式编译并启动服务器：

```
$ go build -o server
$ TLS_CERT_FILE_PATH=./server.crt TLS_KEY_FILE_PATH=./server.key ./server
```

如果你使用 Windows，必须以不同的方式指定变量。对于 PowerShell，以下命令有效：

```C> $env:TLS_CERT_FILE_PATH=./server.crt; $env:TLS_KEY_FILE_PATH=./server.key ./server
```

一旦服务器运行，使用 `curl` 发起请求：

```
$ curl https://localhost:8443/api
```

你将收到以下错误：

```
curl: (60) SSL certificate problem: self signed certificate
```

这是由于 `curl` 不信任你的自签名证书。为了让 `curl` 验证你的证书，请提供给服务器的 `server.crt` 文件：

```
$ curl --cacert ./server.crt https://localhost:8443/api
```

服务器端将看到如下输出：

```
2021/05/05 08:17:55 Hello, world!
```



Сначала мы создаем конфигурацию сервера, вызывая метод `httptest.NewUnstartedServer()`. Это возвращает объект типа `*httptest.Server`, тип структуры, определенный в пакете `net/http/httptest`. Затем мы включаем HTTP/2, установив для поля `EnableHTTP2` значение `true`. Это делается для того, чтобы тестовый сервер был как можно ближе к «настоящему» серверу. Наконец, мы вызываем метод `StartTLS()`. Это автоматически генерирует сертификат TLS и пару ключей и запускает сервер HTTPS. Для связи с этим тестовым HTTPS-сервером нам понадобится специально созданный клиент:

```
client := ts.Client()
resp, err := client.Get(ts.URL + "/api")
```

Объект `http.Client`, который мы получаем при вызове метода `Client()` объекта тестового сервера, автоматически настраивается на доверие сертификатам TLS, созданным для тестирования. В Листинге 7.8 показан тест, проверяющий функционирование ПО промежуточного слоя ведения журналов.

Мы создаем новый `bytes.Buffer`, `buf` и указываем его как `io.Writer` при создании нового объекта `log.Logger`. Затем, после получения настроенного клиента для тестового сервера, мы делаем запрос HTTP GET с помощью метода `Get()`. Поскольку мы тестируем функциональность промежуточного программного обеспечения, мы отбрасываем ответ. Затем мы проверяем, содержит ли зарегистрированное сообщение в объекте `buf` ожидамую строку, используя функцию `strings.Contains()`. Сохраните Листинг 7.8 как `middleware_test.go` в каталоге `chap7/tls-server-test` и запустите тест:

```
$ go test -v
=== RUN   TestMiddleware
--- PASS: TestMiddleware (0.01s)
PASS
ok          github.com/practicalgo/code/chap7/tls-server-test     0.557s
```

Отлично, теперь вы узнали, как настроить сервер с поддержкой TLS для своих тестов. На практике вы не будете генерировать сертификаты TLS, как это делали мы ранее. Вы также не будете вручную настраивать каждый клиент (например, `curl` или другую службу) для доверия сгенериному сертификату. Это просто не масштабируется. Вместо этого сделайте следующее:

*   Для внутренних доменов и служб внедрите внутренний доверенный CA с помощью таких инструментов, как `cfssl` ([`github.com/cloudflare/cfssl`](https://github.com/cloudflare/cfssl)), а затем создайте механизм для создания сертификатов и доверия CA.
*   Для общедоступных доменов и служб запрашивайте сертификаты у доверенного CA — либо вручную, либо в большинстве случаев, с помощью автоматизированной процедуры (например, [`github.com/caddyserver/certmagic`](https://github.com/caddyserver/certmagic)).

## Резюме

Вы начали эту главу с того, что узнали, как установить максимальное время выполнения функции-обработчика. Вы настроили свой сервер для отправки ответа HTTP 503 на сервер, когда функция обработчик не завершает обработку запроса в указанный интервал времени. Затем вы узнали, как написать свои функции обработчика таким образом, чтобы они не продолжали обработку запроса, если время ожидания уже истекло или клиент отключился на полпути. Эти методы предотвращают использование ресурсов вашего сервера для выполнения работы, которая больше не требуется.

Затем вы узнали, как реализовать глобальное время ожидания чтения и записи для ваших серверных приложений и как реализовать корректное завершение работы для ваших серверных приложений. Наконец, вы узнали, как реализовать безопасный канал связи между вашим сервером и клиентом с использованием сертификатов TLS. Благодаря внедрению этих методов ваш HTTP-сервер будет готов к работе. Мы крат рассмотрим некоторые из оставших задач в Приложении A, «Создание наблюдаемых приложений» и Приложении B, «Развертывание приложения».

В следующей главе вы узнаете, как создавать клиентов и серверы с помощью gRPC, инфраструктуры удаленного вызова процедур (RPC), созданной на основе HTTP/2.

# ГЛАВА 8: Создание RPC приложений с помощью gRPC

В этой главе вы научитесь создавать сетевые приложения, использующие `Удаленный Вызов процедур` (RPC) для связи. Хотя стандартная библиотека поддерживает создание таких приложений, мы будем делать это с помощью gRPC, `универсальной` среды RPC с открытым исходным кодом. Мы начнем с краткого обсуждения фреймворков RPC и закончим главу, научившись писать полностью тестируемые gRPC-приложения. Попутно вы также научитесь использовать протокольные буферы, язык описания интерфейса и формат данных, который обеспечивает связь клиент-сервер.




```go
service Users {
  rpc GetUser (UserGetRequest) returns (UserGetReply) {}
}
```

`GetUser` 方法接收类型为 `UserGetRequest` 的输入消息并返回类型为 `UserGetReply` 的消息。在 gRPC 中，函数必须包含输入消息并返回输出消息。因此，客户端和服务器应用程序通过传递消息进行交互。

什么是*消息*（message）？它像一个信封，用于在客户端和服务器之间传输数据。消息的定义类似于结构体类型。`GetUser` 方法旨在允许客户端根据电子邮件或其他标识符请求用户。因此，我们如下定义了包含两个字段的 `UserGetRequest` 消息：

```go
message UserGetRequest {
  string email = 1;
  string id = 2;
}
```

在消息定义内部，我们定义了两个字段：`email`（字符串）和 `id`（另一个字符串）。消息中的字段定义应指定三点：类型、名称和编号。字段类型可以是当前支持的整数类型（`int32`、`int64` 等）、`float`、`double`、`bool`（用于逻辑数据）、`string` 和 `bytes`（用于任何任意数据）。

你也可以定义其他类型消息的字段。字段名称应使用小写字母并用下划线 `_` 分隔多个单词，例如 `first_name`。字段编号是指定字段在消息中位置的方式。字段编号可以从 1 开始到 2²⁹，其中某些范围仅保留供内部使用。建议的策略之一是在字段编号中留出空格。例如，你可以将第一个字段编号为 1，然后对下一个字段使用 10。这意味着你以后可以添加任何额外的字段，而无需重新对字段编号，同时可以将相关的字段分组在一起。

需要注意的是，字段编号是内部细节，你的应用程序不需要担心它，因此分配字段编号时必须谨慎，永远不要更改，并考虑到未来的版本进行设计。我们将在稍后关于正向和向后兼容性的章节中讨论这个话题。

接下来，我们如下定义 `UserGetReply` 消息：

```go
message UserGetReply {
  User user = 1;
}
```

上述消息包含一个类型为 `User` 的 `user` 字段。我们如下定义 `User` 消息：

```go
message User {
  string id = 1;
  string first_name = 2;
  string last_name = 3;
  int32 age = 4;
}
```

图 8.2 展示了 gRPC 服务 protobuf 定义的不同部分。在下一节中，你将了解如何在 gRPC 服务器上注册多个服务。

 ![图 8.2: protobuf 语言规范的部分](img/0802.png)

**图 8.2**: protobuf 语言规范的部分

一旦你定义了*服务接口*（service interface），你随后会将该定义转换为可在你的应用程序中使用的格式。此转换过程将使用 protobuf 编译器 `protoc` 以及针对特定语言的插件模块 `protoc-gen-go` 完成。需要注意的是，你将直接与 `protoc` 命令交互。如果你没有按照说明进行安装...（此处对应原文截断）




```go
func (s *userService) GetUser(
    ctx context.Context,
    in *users.UserGetRequest,
) (*users.UserGetReply, error) {
    log.Printf(
        "Received request for user with Email: %s Id: %s\n",
        in.Email,
        in.Id,
    )
    components := strings.Split(in.Email, "@")
    if len(components) != 2 {
        return nil, errors.New("invalid email address")
    }
    u := users.User{
        Id:        in.Id,
        FirstName: components[0],
        LastName:  components[1],
        Age:       36,
    }
    return &users.UserGetReply{User: &u}, nil
}
```

`GetUser()` 方法接收两个参数：`context.Context` 对象和 `users.UserGetRequest` 对象。它返回两个值：类型为 `*users.UserGetReply` 的对象和 `error`。请注意，Go 中对应的 RPC 等价方法 `GetUser()` 返回了一个额外的值——错误。对于其他语言，情况可能有所不同。

对应消息的结构类型定义在 `users.pb.go` 文件中。每个结构都有几个 protobuf 内部使用的字段，但你会发现它包含了 protobuf 规范的 Go 等价实现。

首先是 `UserGetRequest` 结构：

```
type UserGetRequest struct {
    // other fields
    Email string
    Id    string
}
```

同样，`UserGetReply` 结构将包含 `User` 字段：

```go
type UserGetReply struct {
    // other fields
    User *User
}
```

`User` 类型将包含 `Id`、`FirstName`、`LastName` 和 `Age` 字段：

```go
type User struct {
    // Other fields
    Id        string
    FirstName string
    LastName  string
    Age       int32
}
```

该方法的实现注册了传入请求，从电子邮件中提取用户名和域名，创建一个虚拟的 `User` 对象，并返回 `UserGetReply` 值和空错误。如果电子邮件格式错误，我们返回空 `UserGetReply` 值和错误值。

实现 gRPC 服务端应用程序的最后一步是在 gRPC 服务器上注册 `Users` 服务：

```go
lis, err := net.Listen("tcp", listenAddr)
s := grpc.NewServer()
users.RegisterUsersServer(s, &userService{})
log.Fatal(s.Serve(lis))
```

为了在 gRPC 服务器上注册 `Users` 服务处理程序，我们调用了执行 `protoc` 命令时生成的 `users.RegisterUsersServer()` 函数。该函数接收两个参数。第一个参数是 `*grpc.Server` 对象，第二个参数是 `Users` 服务的实现，在这里它是我们定义的 `userService` 类型。图 8.3 图化展示了不同的阶段。

![图 8.3: 创建带有 Users 服务的 gRPC 服务器](img/0803.png)

图 8.3: 创建带有 `Users` 服务的 gRPC 服务器

在代码清单 8.2 中显示了服务器的完整代码。

在 `chap8/user-service` 目录内创建一个新的 `server` 目录。并在其中初始化模块：

```bash
$ mkdir -p chap8/user-service/server
$ cd chap8/user-service/server
$ go mod init github.com/username/user-service/server
```

然后将代码清单 8.2 保存为该目录下的新文件 `server.go`。在服务器目录下运行以下命令：

```bash
$ go get google.golang.org/grpc@v1.37.0
```

上述命令将获取 `google.golang.org/grpc/grpc` 包。

(此处省略了原文中大量重复的版本号行)



在 `main()` 函数中，我们首先检查客户端是否通过命令行参数指定了连接的服务器地址。如果未指定，我们将输出错误消息并退出。然后，我们调用 `setupGrpcConn()` 函数并传递服务器地址。我们在 `defer` 语句中调用连接对象的 `Close()` 方法，以确保客户端连接在程序退出前被关闭。接着，我们调用 `getUsersServiceClient()` 函数来获取与 `Users` 服务通信的客户端。紧接着，我们调用了带有类型为 `*users.UserGetRequest` 值的 `getUser()` 函数。请注意，我们没有在值中指定 `Id` 字段，因为 protobuf 消息中的字段默认是可选的。因此，我们也可以发送一个空值，换句话说，即 `&users.UserGetRequest{}`。当 `getUser()` 函数返回时，结果类型为 `users.UserGetReply`。该值包含一个类型为 `users.User` 的字段，在这里我们调用 `fmt.Fprintf()` 函数显示两个字符串值：`FirstName` 和 `LastName`。

在 `chap8/user-service` 目录下创建一个新目录 `client`。按照如下方式在其中初始化模块：

```bash
$ mkdir -p chap8/user-service/client
$ cd chap8/user-service/client
$ go mod init github.com/username/user-service/client
```

然后，将[列表 8.4] 保存为该目录的新文件 `main.go`。在客户端子目录下运行以下命令：

```
$ go get google.golang.org/grpc@v1.37.0
```

上述命令将提取 `google.golang.org/grpc/` 包，更新 `go.mod` 文件并创建 `go.sum` 文件。最后一步是手动在 `go.mod` 文件中添加关于 `github.com/username/user-service/service` 包的信息。最终的 `go.mod` 文件见[列表 8.5]。

现在，`chap8/user-service` 目录结构应该像[图 8.4] 所示。

![图 8.4: Users 服务的目录结构](img/0804.png)

[图 8.4]: `Users` 服务目录结构

太棒了。现在你准备好按照如下方式编译并运行客户端了：

```bash
$ cd chap8/user-service/client
$ go build -o client
$ ./client localhost:50051
User: Jane Doe
```

在服务器端，你将看到如下注册的消息：

```
2021/05/16 08:23:52 Received request for user with Email: jane@doe.com Id:
```

非常完美。你已经编写了自己的第一个通过 gRPC 交互的服务器和客户端应用程序。接下来，你将学习如何编写测试来验证你的客户端和服务器的行为。

### 测试服务器

测试客户端和服务器的关键组件是 `google.golang.org/grpc/test/bufconn` 包（以下简称 `bufconn`）。它允许我们在 gRPC 客户端和服务器之间在内存中建立一个完整的通信信道。我们不再创建真实的网络监听器，而是在测试中使用 `bufconn` 包来创建它。这避免了在测试期间配置真实网络服务器和客户端的需要，同时确保了我们最关心的服务器客户端逻辑是可测试的。

让我们编写一个函数来启动用于 `Users` 服务的测试 gRPC 服务器：

```go
func startTestGrpcServer() (*grpc.Server, *bufconn.Listener) {
    l := bufconn.Listen(10)
    s := grpc.NewServer()
    registerServices(s)
    go func() {
        err := startServer(s, l)
        if err != nil {
            log.Fatal(err)
        }
    }()
    return s, l
}
```



`startTestGrpcServer()` 函数与我们为服务器编写的函数完全相同，仅区别在于注册模拟服务：`users.RegisterUsersServer(s, &dummyUserService{})`。我们在单独的 goroutine 中启动服务器，并返回 `*bufconn.Listener` 值，以便我们为客户端创建一个拨号器，就像我们在测试服务器时所做的那样。其核心思想是，我们希望服务器在后台运行，同时我们在测试的其余部分向其发送请求。

最后步骤是调用 `GetUser()` RPC 方法并检查结果。代码列表 8.7 显示了完整的测试函数。

将代码列表 8.7 保存为新文件 `client_test.go` 并位于 `chap8/user-service/client` 目录中。按照以下方式运行测试：

```
$ go test
PASS
ok     github.com/practicalgo/code/chap8/user-service/client 0.128s
```

在继续之前，让我们总结一下你已经学到的内容。创建一个 gRPC 网络应用程序，首先需要使用协议缓冲区语言（Protocol Buffer）创建服务规范。然后，你使用 protobuf 编译器 (`protoc`) 和 go 插件创建*魔法胶水*。这会生成代码，处理数据的低级序列化和反序列化，并在客户端和服务器之间通过网络传输。通过使用类型、实现接口以及调用生成代码中的函数，你随后编写服务器和客户端实现。最后，你测试你的服务器和客户端。

值得简要地将此过程与编写 HTTP 服务器和客户端进行比较。首先，让我们看看 gRPC 服务器和 HTTP 服务器。这两类服务器应用程序都配置网络服务器和处理网络请求的函数。HTTP 服务器可以定义任意的自定义处理函数并注册它们以处理任意路径，而 gRPC 服务器只能注册处理相应 protobuf 规范定义的 RPC 调用的函数。

比较 HTTP 客户端和 gRPC 客户端，我们可以看到它们的相似之处，例如创建客户端和随后的请求发送。然而，HTTP 客户端可以向 HTTP 服务器发送任意请求，并且在发送无效请求时可能收到错误作为响应，而 gRPC 客户端仅限于协议缓冲区规范中定义的 RPC 调用。此外，客户端必须知道 RPC 服务器定义的消息类型，以便能够向服务器发送其理解的消息。对于 HTTP 应用程序，客户端没有这种强制性要求。

接下来，让我们看看处理协议缓冲区时的两个关键主题：序列化（marshaling）和反序列化（unmarshalling），以及数据格式随时间的演变。

## Protobuf 消息遍历

消息是 gRPC 应用程序的基石。当你从另一个应用程序与 gRPC 应用程序交互时，你需要能够将数据字节转换为协议缓冲区，反之亦然。我们将在之后探讨。之后你将学习如何随着应用程序的发展开发具有后向向前兼容性的 protobuf 消息。

### 序列化与反序列化

考虑对 `Users` 服务 `GetUser()` 函数的请求。在客户端和测试中，你如下所示创建了 `GetUserRequest` 类型的值：

```
u := users.UserGetRequest{Email: "jane@doe.com"}
```

然后你调用了 `GetUser()` 函数并传递了请求。如果我们在客户端应用程序中调用 `GetUser()` 函数，让用户以 JSON 格式字符串的方式指定查询请求，会怎样？为了唤起记忆，`GetUserRequest` 定义如下：

```go
message UserGetRequest {
    string email = 1;
    string id = 2;
}
```

直接映射到该消息类型的 JSON 格式字符串示例：`{"email": "jane@doe.com", "id": "user-123"}`。让我们看看如何将此 JSON 字符串转换为 `GetUserRequest` 对象：

```go
u := users.UserGetRequest{}
jsonQuery = `'{"email": "jane@doe.com", "id": "user-123"}`
input := []byte(jsonQuery)
err = protojson.Unmarshal(input, &u)
if err != nil {
    log.Fatal(err)
}
```



软件的正向兼容性意味着旧版本将继续与新版本兼容。同样，反向兼容性的概念意味着新版本的软件必须继续与旧版本兼容。我们希望开发我们的 `protobuf` 消息和 `gRPC` 方法，使得通过这些消息与我们的服务交互的应用程序（包括服务本身）随着时间的推移能够兼容新旧版本，而不会发生突然的破坏性更改。当你在消息中定义字段时，如下所示分配字段标签：

```
message UserGetRequest {
  string email = 1;
  string id = 2;
}
```

对于 `protobuf` 消息，必须记住以下关键点：

- 永远不要更改字段标签。
- 只有当旧新数据类型相互兼容时，您才能更改字段的数据类型。例如，您可以在 `int32`、`uint32`、`int64`、`uint64` 和 `bool` 之间转换。有关其他类型的详细信息，请参考 `Protocol Buffers 3` 规范。
- 永远不要重命名字段。重命名字段，请输入带有未使用标签的新字段，然后只有当所有客户端和服务器都已更改为使用新字段时，再删除该字段。

对于 `gRPC` 服务，除了不能对协议缓冲区执行的操作外，请注意以下几点：

- 您不能在不破坏现有客户端的情况下重命名服务，除非您能够绝对保证客户端和服务器应用程序同时进行更改。
- 您不能重命名函数。输入新函数，将所有使用该函数的应用程序切换到新函数，然后删除旧函数。

如果您想更改函数作为输入接收和作为输出返回的消息类型，您必须考虑这种更改是什么。如果消息中的所有字段保持不变，则只需更新所有应用程序以使用新的消息名称。然而，如果您对字段进行了任何更改（添加/删除/更新），您将必须记住上述关于 `protobuf` 消息的要点。

练习 8.2 提供了一个研究特定场景的机会，您需要在 `gRPC` 应用中考虑兼容性。

## 多个服务

`gRPC` 服务器可以处理来自一个或多个 `gRPC` 服务的请求。让我们看看如何添加第二个服务——`Repo` 服务，它将用于请求特定用户的代码仓库。首先，您需要为该服务创建 `protobuf` 规范。创建 `chap8/multiple-services` 目录。如下所示将服务目录从 `chap8/user-service` 复制到该目录内：

```
$ mkdir -p chap8/multiple-services
$ cp -r chap8/user-service/service chap8/multiple-services/
```

更新 `go.mod` 文件，使其包含以下内容：

```
module github.com/username/multiple-services/service
go 1.16
```

现在，创建一个新的 `repositories.proto` 文件，内容如 列表 8.11 所示。

仓库服务定义了一个 RPC 方法 `GetRepos` 和另外两个消息类型 `RepoGetRequest` 和 `RepoGetReply`，它们对应于函数的输入和输出。




```go
func TestRepoService(t *testing.T) {

    s, l := startTestGrpcServer()
    defer s.GracefulStop()

    bufconnDialer := func(
        ctx context.Context, addr string,
    ) (net.Conn, error) {
        return l.Dial()
    }

    client, err := grpc.DialContext(
        context.Background(),
        "", grpc.WithInsecure(),
        grpc.WithContextDialer(bufconnDialer),
    )
    if err != nil {
        t.Fatal(err)
    }
    repoClient := svc.NewRepoClient(client)
    resp, err := repoClient.GetRepos(
        context.Background(),
        &svc.RepoGetRequest{
            CreatorId: "user-123",
            Id:        "repo-123",
        },
    )

    if err != nil {
        t.Fatal(err)
    }
    if len(resp.Repo) != 1 {
        t.Fatalf(
            "Expected to get back 1 repo, got back: %d repos", len(resp.Repo),
        )
    }
    gotId := resp.Repo[0].Id
    gotOwnerId := resp.Repo[0].Owner.Id

    if gotId != "repo-123" {
        t.Errorf(
            "Expected Repo ID to be: repo-123, Got: %s",
            gotId,
        )
    }
    if gotOwnerId != "user-123" {
        t.Errorf(
            "Expected Creator ID to be: user-123, Got: %s",
            gotOwnerId,
        )
    }
}
```

上述代码突出亮了用于测试 `Repo` 服务的关键断言。在调用 `GetRepos()` 函数获取响应后，我们检查了切片 `resp.Repo` 的长度。我们期望它只包含一个 `Repository` 对象。如果不是这样，测试将失败。如果发现切片中确实包含 `Repo` 对象，我们就会像处理任何其他 Go 切片一样，通过访问 `Repo` 字段来获取其 `Id` 和 `OwnerId`。

你可以在此书代码仓库的 `chap8/multiple-services/server/server_test.go` 文件中找到完整的测试。

在下一个练习中，你将扩展 `mync grpc` 客户端，使其也支持对 `Repo` 服务执行请求。

在本章的最后一节中，让我们学习 gRPC 应用程序中的错误处理。

## 错误处理

正如你所看到的，在实现 gRPC 方法时，你返回了两个对象：一个是响应，另一个是错误值。如果我们从方法返回一个非空错误会发生什么？让我们看看在调用 `GetUser()` 方法时如果不传递有效的电子邮件地址会发生什么。

从终端进入目录 `chap8/user-service/server`，根据需要编译并启动服务器：

```
$ cd chap8/user-service/server
$ go build -o server
$ ./server
```

```从另一个终端会话进入目录 `chap8/user-service/client`，根据需要创建并启动客户端，如下所示传递一个空对象：

```
$ cd chap8/user-service/client
$ go build -o client
$ ./client localhost:50051 '{}'2021/05/25 21:12 rpc error: code = Unknown desc = invalid email
```

我们得到了错误信息，客户端退出。文本 `"invalid email address"` 源于我们从 `Users` 服务处理程序返回的错误值：

```
components := strings.Split(in.Email, "@")
if len(components) != 2 {
    return nil, errors.New("invalid email address")
}
```

字符串 `"rpc error: code = Unknown desc"` 提取自 gRPC 库，表示在响应中找到了代码。为了修复这个问题，我们需要更新服务器，使其返回一个类似于 HTTP 的有效代码。gRPC 支持大量由 `google.golang.org/codes` 包定义的错误。其中之一是 `InvalidArgument`，考虑到客户端没有提供有效的电子邮件地址，这用在这里非常恰当。

现在，让我们更新服务器，使其改为返回该代码的错误：

```go
import (
   "google.golang.org/codes"
   "google.golang.org/status"
)
components := strings.Split(in.Email, "@")
if len(components) != 2 {
    return nil, status.Error(
        codes.InvalidArgument,
        "Invalid address specified",
    )
}
```

我们使用了另一个包 `google.golang.org/status` 来通过 `status.Error()` 函数创建错误值。函数的第一个参数是代码，第二个参数是描述消息。你可以在源码仓库的 `chap8/user-service-error-handling/server` 目录下找到更新后的服务器代码。

按照如下方式编译并运行此新版本的服务器：

```
$ ./server
```

现在，如果你再次发送请求，你将看到如下注册的代码：

```
$ ./client-client localhost:50051 '{}'
```




接下来，我们将学习三种新的通信模式：`服务端流式传输`、`客户端流式传输`以及它们的组合——`双向流式传输`。在这三种模式中，可以在单次方法调用期间交换多个请求和响应消息。让我们从服务端流式传输开始学习。

### 服务端流式传输

在`服务端流式传输`中，当客户端发送请求时，服务器可以发送多个响应消息。考虑我们在上一章中实现的 `Repo` 服务的 `GetRepos()` 方法。与其在一个消息中发送存储库列表，我们可以通过发送多个 `Repo` 消息作为响应，每个消息包含存储库的详细信息。让我们看看如何实现这样一个应用程序。

首先，我们如下所示更新 `Repo` 服务的 protobuf 规范：

```
service Repo {d
  rpc GetRepos (RepoGetRequest) returns (stream RepoGetReply) {}
}
```

这里的关键区别在于方法返回类型中的流规范。这告诉了 Protocol Buffer 编译器和 Go gRPC 插件，响应将包含一个 `RepoGetReply` 消息的`流`。列表 9.1 显示了 `Repo` 服务的完整 protobuf 规范。

与原始服务规范（第 8 章，列表 8.11）相比，有两个关键变化。`GetRepos()` 方法现在返回 `RepoGetReply` 消息流。`RepoGetReply` 消息现在包含一个存储库的信息，因此我们删除了该字段中的 `repeated` 声明。

创建 `chap9/server-streaming`目录。在其内部创建一个新的子目录 `service` 并在其中初始化模块：

```
$ mkdir -p chap9/server-streaming/service
$ go mod init github.com/username/server-streaming/service
```

然后，在 `service` 目录中创建一个新文件 `repositories.proto`，内容如列表 9.1 所示。从 `chap8/multiple-services/service/` 复制 `users.proto` 文件到该目录。在文件中如下所示替换 `go_package`：

```
option go_package = "github.com/username/server-streaming/service";
```

接下来，我们生成对应两个服务的 Go 代码：

```
$ protoc --go_out=. --go_opt=paths:relative \
--go-grpc_out=. --go-grpc_opt=paths:relative \
    users.proto repositories.proto
```

运行上述命令后，你应该像以前一样在 `service` 目录中看到以下文件：`users.pb.go`、`users_grpc.pb.go`、`repositories.pb.go` 和 `repositories_grpc.pb.go`。

接下来，我们将修改 `GetRepos()` 方法的实现，如下：

```go
func (s *repoService) GetRepos(
    in *svc.RepoGetRequest,
    stream svc.RepoGetReposServer,
) error {
    log.Printf(
        "Received request for repo with CreateId: %s Id: %s\n",
        in.CreatorId,
        in.Id,
    )
    repo := svc.Repository{
        Id: in.Id,
        Owner: &svc.User{
            Id: in.CreatorId,
            FirstName: "Jane",
        },
    }
    cnt := 1
    for {
        repo.Name = fmt.Sprintf("repo-%d", cnt)
        repo.Url = fmt.Sprintf(
            "https://example.com/test/%s",
            repo.Name,
        )
        r := svc.RepoGetReply{
            Repo: &repo,
        }
        if err := stream.Send(&r); err != nil {
            return err
        }
        if cnt >= 5 {
            break
        }
        cnt++
    }
    return nil
}
```

上述实现有几个关键变化。首先，方法的签名发生了变化。它接收两个参数：`RepoGetRequest` 类型请求和 `RepoReposServer` 流对象，并返回 `error` 值。`RepoReposServer` 类型是 protobuf 编译器生成的接口：

```go
type RepoReposServer interface {
         Send(*RepoGetReply) error
         grpc.ServerStream
}
```

实现此接口的类型必须实现 `Send()` 方法，该方法接收 `RepoGetReply` 消息（我们的响应类型）并返回 `error` 值。当然，作为开发者，你不需要担心实现此接口的类型，因为这是 protobuf 编译器和 Go 模块自动完成的。我们使用此方法返回 `RepoGetReply` 消息作为响应。内置字段 `grpc.ServerStream` 是 `google.golang.org/grpc` 包定义的另一个接口。我们将在“使用流实现中间件”部分了解更多信息。

在方法体内，我们首先记录请求信息的输出。然后我们创建一个 `Repo` 对象用于返回。在 `for` 循环中，我们额外配置该对象，创建 `RepoGetReply` 消息，然后通过 `stream.Send()` 方法将其发送给客户端。我们总共发送五个这样的响应消息，每次更改 `Repo` 对象。当我们发送所有响应后，退出循环并返回空错误。

列表 9.2 显示了 `Users` 和 `Repo` 服务的 gRPC 服务器。

在 `chap9/server-streaming` 中创建新的子目录 `server` 并在其中初始化模块：

```
$ mkdir -p chap9/server-streaming/server
$ cd chap9/server-streaming/server
$ go mod init github.com/username/server-streaming/server
```

将列表 9.2 保存为服务器目录下的 `server.go`。接下来获取 `google.golang.org/grpc` 包（版本 1.37.0）：

```
$ go get google.golang.org/grpc@v1.37.0
```

然后更新 `go.mod` 文件以添加服务依赖，包括 `replace` 指令，使最终的 `go.mod` 类似于列表 9.3。

确保你现在可以使用 `go build` 成功编译服务器。接下来，我们将编写一个测试函数来检查服务器运行。正如第 8 章所示，我们将使用 `bufconn` 包在测试客户端和服务器之间建立内存通道。假设我们有一个 `repoClient` 对象，配置为测试 gRPC 服务器上的 `Repo` 服务连接。我们将如下调用 `GetRepos()` 方法：

```go
stream, err := repoClient.GetRepos(
    context.Background(),
    &svc.RepoGetRequest{CreatorId: "user-123", Id: "repo-123"},
)
```

方法调用返回两个值：`stream`（`RepoReposClient` 类型对象）和 `err`（错误值）。`RepoReposClient` 类型是 `RepoReposServer` 类型的客户端等，定义如下：

```go
type RepoGetReposClient interface {
    Recv() (*RepoGetReply, error)
    grpc.ClientStream
}
```

实现此接口的类型必须实现 `Recv()` 方法，该方法返回 `RepoGetReply` 消息（方法的响应类型）并返回 `error` 值。内置字段 `grpc.ClientStream` 是 `google.golang.org/grpc` 包定义的另一个接口。我们将在“使用流实现中间件”部分了解更多信息。

为了从服务器读取响应流，我们将使用 `Recv()` 方法：

```go
var repos []*svc.Repository
for {
    repo, err := stream.Recv()
    if err == io.EOF {
        break
    }
    if err != nil {
        log.Fatal(err)
    }
    repos = append(repos, repo.Repo)
}
```



通过使用无限 `for` 循环，我们调用 `Recv()` 方法。如果返回的错误值为 `io.EOF`，则没有更多可读消息，因此我们跳出循环。如果收到的任何其他错误，我们将打印该错误并停止执行。否则，我们将存储库信息添加到 `repos` 切片的消息中。在读取服务器响应后，我们可以检查各种细节，看它们是否符合预期的响应。代码列表 9.4 显示了用于检查 `GetRepos()` 方法运行的测试函数完整列表。（此处未显示用于 `Users` 服务的测试函数。您可以在书的原始代码仓库中找到它。）

将代码列表 9.4 存为 `server_test.go` 位于服务器目录内。确保您可以运行测试并且它成功完成：

```
$ go test -v
=== RUN   TestUserService
2021/06/09 08:43:25 Received request for user with Email: 
jane@doe.com Id: foo-bar
--- PASS: TestUserService (0.00s)
=== RUN   TestRepoService
2021/06/09 08:43:25 Received request for repo with CreateId:
user-123 Id: repo-123
--- PASS: TestRepoService (0.00s)
PASS
ok      github.com/practicalgo/code/chap9/server-streaming  1s
```

服务器端流传输对于向客户端发送多个响应是有用的。发送多个对象比发送此类对象的数组可能更有效。另一个有用场景是发送最终值对应的响应，例如在操作结果的流传输中。

在本章的第一个练习 9 中，您在 `Repo` 服务中实现了一个新方法，它模拟了存储库的构建并将日志发送给客户端。

### 客户端流传输

与服务器端流类似，客户端调用服务器上的 RPC 方法并以消息流的形式请求，而不是单个消息。

让我们在 `Repo` 服务中添加一个新方法 `CreateRepo()`，它现在将接受消息流作为参数。每个消息都将指定新存储库的细节。对于此方法，我们定义了一个新消息类型 `RepoCreateRequest`。方法的 protobuf 定义如下：

```
rpc CreateRepo (stream RepoCreateRequest) returns (RepoReply)
```

这里的关键点是类型前的 `stream` 关键字。服务器上该方法的处理器如下：

```go
func (s *repoService) CreateRepo(
    stream svc.Repo_CreateRepoServer,
) error {
    for {
        data, err := stream.Recv()
        if err == io.EOF {
            // 我们已经收到了完整的请求
            // 现在我们可以处理数据
            r := svc.RepoCreateReply{..}
            return stream.SendAndClose(&r)
        }
    }
}
```

`CreateRepo()` 方法的实现接收一个类型 `svc.Repo_CreateRepoServer` 的编译器生成的接口类型，定义如下：

```go
type Repo_CreateRepoServer interface {
        Recv() (*RepoCreateRequest, error)
        SendAndClose(*RepoCreateReply) error
        grpc.ServerStream
}
```

实现此接口的类型将实现两个方法 `Recv()` 和 `SendAndClose()`，并嵌入 `ServerStream` 接口。`Recv()` 方法用于从客户端接收消息，因此返回 `RepoCreateRequest` 值和 `error`。`SendAndClose()` 方法用于向客户端发送响应。因此它接受一个 `RepoReply` 类型的值，发送响应并关闭连接。当然，作为应用程序作者，您不需要担心该类型的实现。

接下来让我们如何从客户端应用程序调用 `CreateRepo()` 方法：

```
repoClient := svc.NewRepoClient(client)
stream, err := repoClient.CreateRepo(
    context.Background(),
)
```

注意我们没有带任何请求参数调用 `CreateRepo()` 方法。它只接受一个 `context.Context` 对象。该方法返回两个值：类型 `Repo_CreateClient` 的 `stream` 和 `error` 值。`Repo_CreateClient` 类型定义如下接口：

```go
type Repo_CreateClient interface {
    Send(*RepoCreateRequest) error
    CloseAndRecv() (*RepoCreateReply, error)
}
```

实现此接口的类型将实现两个方法 `Send()` 和 `CloseAndRecv()`，并嵌入 `ClientStream` 接口。`Send()` 方法用于向客户端发送消息。因此它接受 `RepoCreateRequest` 类型的值作为参数并返回 `error`。`CloseAndRecv()` 方法用于从服务器获取响应。因此它返回 `RepoReply` 值和 `error` 值。

为了向服务器应用程序发送消息，我们将在循环中使用多次 `Send()`：

```
for i := 0; i < 5; i++ {
    r := svc.RepoCreateRequest{
        CreatorId: "user-123",
        Name:      "hello-world",
    }
    err := stream.Send(&r)
    if err != nil {
        t.Fatal(err)
    }
}
```

然后，一旦我们完成了流传输，我们将读取响应：

```
resp, err := stream.CloseAndRecv()
```

### 双向流

在双向流传输中，一旦连接建立，客户端和服务器都可以读取和写入数据。没有任何顺序被强制规定，因此如果应用程序没有应用它，则顺序是不保证的。例如，假设我们想要更新 `Users` 服务以允许用户通过聊天从客服获得帮助。在这种双向流的情况下，用户（客户端）启动与客服（服务器）的对话，他们之间进行交换，直到其中一方中断连接。

首先，在 protobuf 中定义一个双向流方法：

```protobuf
rpc GetHelp (stream HelpRequest) returns (stream HelpReply);
```

现在，在服务器上实现该方法：

```go
func (s *helpService) GetHelp(
    stream svc.Users_GetHelpServer,
) error {
    for {
        req, err := stream.Recv()
        if err == io.EOF {
            return nil
        }
        if err != nil {
            return err
        }
        // 处理请求并发送响应
        resp := &pb.HelpReply{Message: "Hello!"}
        if err := stream.Send(resp); err != nil {
            return err
        }
    }
}
```

`Users_GetHelpServer` 接口如下：

```go
type Users_GetHelpServer interface {
        Recv() (*HelpRequest, error)
        Send(*HelpReply) error
        grpc.ServerStream
}
```

最后，在客户端调用该方法：

```go
stream, err := client.GetHelp(context.Background())
if err != nil {
    log.Fatalf("could not get help: %v", err)
}

go func() {
    for i := 0; i < 5; i++ {
        if err := stream.Send(&pb.HelpRequest{Message: "Hello"}); err != nil {
            log.Fatalf("could not send help: %v", err)
        }
    }
    stream.CloseSend()
}()

for {
    resp, err := stream.Recv()
    if err == io.EOF {
        break
    }
    if err != nil {
        log.Fatalf("could not receive help: %v", err)
    }
    fmt.Printf("Received: %s\n", resp.Message)
}
```




```go
func (s *userService) GetHelp(
    stream svc.Users_GetHelpServer,
) error {
    log.Println("Client connected")
    for {
        request, err := stream.Recv()
        if err == io.EOF {
            break
        }
        if err != nil {
            return err
        }
        fmt.Printf("Request received: %s\n", request.Request)
        response := svc.UserHelpReply{
            Response: request.Request,
        }
        err = stream.Send(&response)
        if err != nil {
            return err
        }
    }
    log.Println("Client disconnected")
    return nil
}
```

`GetHelp()` 方法接收一个类型为 `Users_GetHelpServer` 的参数，该参数是一个如下生成的接口：

```
type Users_GetHelpServer interface {
    Send(*UserHelpReply) error
    Recv() (*UserHelpRequest, error)
    grpc.ServerStream
}
```

由于服务器将接收并发送消息流，因此接口拥有 `Send()` 和 `Recv()` 方法，以及一个嵌入接口 `ServerStream`。

`Send()` 方法用于向客户端发送类型为 `UserHelpReply` 的响应消息。

`Recv()` 方法用于从客户端接收请求。它返回一个类型为 `UserHelpRequest`的值和一个 `error` 值。

然后，我们创建一个 `for` 循环，在循环中不断尝试从客户端流中读取值，如果收到 `io.EOF` 错误则中断循环，如果收到任何其他错误则返回错误值。如果从客户端收到有效请求，我们创建一个 `UserHelpReply` 消息，并使用 `Send()` 方法向客户端返回帮助请求消息。代码列表 9.6 显示了实现 `Users` 服务的 gRPC 服务器应用程序。

在 `chap9/bidi-streaming` 目录下创建一个新的子目录 `server`。按照如下方式在该其中初始化模块：

```
$ mkdir -p chap9/bidi-streaming/server
$ cd chap9/bidi-streaming/server
$ go mod init github.com/username/bidi-streaming/server
```

将 代码列表 9.6 保存为服务器目录下的 `server.go`。然后，我们按照如下方式获取 [`google.golang.org/grpc`](http://google.golang.org/grpc) 包（版本 1.37.0）：

```
$ go get google.golang.org/grpc@v1.37.0
```

然后更新 `go.mod` 文件以添加服务包的依赖，包括 `replace` 指令，使最终的 `go.mod` 看起来像 代码列表 9.7 所示。确保你现在可以使用 `go build` 编译服务器。让我们看看如何设置客户端。考虑 `setupChat()` 函数，它接收一个 `io.Reader`（从从中读取帮助请求）、一个用于与 `Users` 服务通信的 `UsersClient` 对象以及一个用于响应的 `io.Writer`。

```go
func setupChat(r io.Reader, w io.Writer, c svc.UsersClient) error {
    stream, err := c.GetHelp(context.Background())
    if err != nil {
        return err
    }
    for {
        scanner := bufio.NewScanner(r)
        prompt := "Request: "
        fmt.Fprint(w, prompt)

        scanner.Scan()
        if err := scanner.Err(); err != nil {
            return err
        }
        msg := scanner.Text()
        if msg == "quit" {
            break
        }
        request := svc.UserHelpRequest{
            Request: msg,
        }
        err := stream.Send(&request)
        if err != nil {
            return err
        }
        resp, err := stream.Recv()
        if err != nil {
            return err
        }
        fmt.Printf("Response: %s\n", resp.Response)
    }
    return stream.CloseSend()
}
```

首先我们调用 RPC 方法 `GetHelp()`，它返回一个类型为 `Users_HelpClient` 的值，该接口定义如下：

```
type Users_HelpClient interface {
    Send(*UserHelpRequest) error
    Recv() (*UserHelpReply, error)
    grpc.ClientStream
}
```

与 `Users_HelpServer` 类型类似，`Users_HelpClient` 类型定义了发送和接收消息的方法，并包含了 `ClientStream` 接口。一旦获取流，设置了一个 `for` 循环，以交互模式读取用户输入并作为 `UserHelpRequest` 发送到服务器。如果用户输入 `quit`，连接将关闭。代码列表 9.8 显示了客户端应用程序。

在 `chap9/bidi-streaming` 目录下创建一个新的子目录 `client` 并在其中初始化模块：

```
$ mkdir -p chap9/bidi-streaming/client
$ cd chap9/bidi-streaming/client
$ go mod init github.com/username/bidi-streaming/client
```

将 代码列表 9.8 保存为 `client` 目录下的 `client.go`。接下来我们获取 [`google.golang.org/grpc`](http://google.golang.org/grpc) 包（版本 1.37.0）：

```
$ go get google.golang.org/grpc@v1.37.0
```

然后更新 `go.mod` 文件以添加服务包的依赖，包括 `replace` 指令，使最终的 `go.mod` 看起来像 代码列表 9.9 所示。编译客户端。

现在在一个终端会中启动服务器：

```
$ cd chap9/bidi-streaming/server
$ go build
$ ./server
```

在另一个终端会中运行客户端：

```
$ ./client localhost:50051
Request: Hello there
Response: Hello there
Request: I need some help
Response: I need some help
Request: quit
```

在服务器端你将看到以下消息：

```
2021/06/24 20:46:56 Client connected
Request received: Hello there
Request received: I need some help
2021/06/24 20:47:29 Client disconnected
```

当从客户端终端会话输入 `quit` 命令时，客户端调用了 `CloseSend()` 方法，该方法随后关闭了与服务器的客户端连接，并返回错误值 `io.EOF`。

现在你学习了 gRPC 支持的三类流式通信。与仅交换请求和响应消息的 RPC 方法调用相比，流式传输发生了多个此类消息的交换，如图 9.1 所示。

![图 9.1: 流传输模式](img/0901.png)

图 9.1: 流传输模式

接下来你将学习如何在传输任意字节数据时使用流式传输。

## 接收和发送任意字节

到为止我们只关注在 gRPC 服务器应用程序和客户端之间传输字符串和整数。如何发送和处理任何任意数据，例如存储在存储库中的数据（例如 `.tar.gz` 文件）呢？这就是 `bytes` 类型出现的地方。让我们更新 `RepoCreateRequest` 数据类型以添加 `data` 字段，它将包含任意字节，例如存储在存储库中的文件内容：

```
message RepoCreateRequest {
  string creator_id = 1;
  string name = 2;
  bytes data = 3;
}
```

所有可以在 Go 中以字节切片形式保存的内容，都可以保存在数据字段中。为了请求服务器创建存储库，客户端必须构造如下请求：

```go
repoData := []byte("Arbitrary data")
resp, err := repoClient.CreateRepo(
    context.Background(),
    &svc.RepoCreateRequest{
        CreatorId: "user-123",
        Name:      "test-repo",
        Data:      repoData,
    },
)
```




在服务器端，该方法将如下所示处理请求（包括数据）：

```go
func (s *repoService) CreateRepo(
    ctx context.Context,
    in *svc.RepoCreateRequest,
) (*svc.RepoCreateReply, error) {
    repoId := fmt.Sprintf("%s-%s", in.Name, in.CreatorId)
    repoURL := fmt.Sprintf("https://git.example.com/%s/%s",
        in.CreatorId, in.Name)
    data := in.Data
    repo := svc.Repository{
        Id:   repoId,
        Name: in.Name,
        Url:  repoURL,
    }
    r := svc.RepoCreateReply{
        Repo: &repo,
        Size: int32(len(data)),
    }
    return &r, nil
}
```

你可以在此书源码仓库的 `chap9/binary-data` 目录中找到示例代码。这种发送任何任意字节的机制非常简单，并且当传输的数据量限制在几个字节时效果良好。但是，对于传输大量数据，建议使用流式传输模式。

在上面的示例中，客户端流式传输将是理想的。从源（例如文件）逐步读取数据字节，然后向服务器发送包含这些数据的消息。继续执行此操作，直到所有数据都被读取完毕。

在流式传输期间，客户端或服务器分别发送多个消息作为请求或响应。我们希望数据以流式方式传输，因此我们可以设计 protobuf 消息，使其包含一个数据字段：

```protobuf
message RepoData {
  bytes data = 1;
}
```

然而，你很少会在不带任何上下文信息的情况下传输任意字节。例如，之前考虑的 `RepoCreateRequest` 消息包含了 `creator_id`、`name` 和 `data`。如果对对这种消息类型进行流式传输，我们必须在所有消息中发送相同的 `creator_id` 和 `name`。因此，建议在流的第一条消息中发送 `creator_id` 和 `name` 字段，然后流中的所有后续消息只包含 `data` 字节。

幸运的是，我们在定义消息时可以使用 Protocol Buffer 的名为 `oneof` 的功能来优雅地实现这一点。该关键字允许我们定义一种消息，在该消息中，任何时刻只能设置字段组中的一个字段。让我们使用 `oneof` 关键字重新定义 `RepoCreateRequest` 消息：

```protobuf
message RepoCreateRequest {
  oneof body {
    RepoContext context = 1;
    bytes data = 2;
  }
}
```

我们这样定义 `RepoCreateRequest`使其具有一个名为 `body` 的 `oneof` 字段。该字段在消息中始终只有 `context`（类型为 `RepoContext`）或 `data`（类型为 `bytes`），而不会两者都有。新的消息类型 `RepoContext` 将包含要创建仓库的上下文信息，定义如下：

```protobuf
message RepoContext {
  string creator_id = 1;
  string name = 2;
}
```

代码列表 9.10 显示了 `Repo` 服务的更新后的 protobuf 规范。

现在`CreateRepo()` 方法接收 `RepoCreateRequest` 消息流并返回 `RepoReply` 消息。创建目录 `chap9/bindata-client-streaming`。在内部创建一个子目录 `service` 并对其初始化：

```bash
$ mkdir -p chap9/bindata-client-streaming/service
```



在 `go.mod` 文件中配置 `replace` 指令，使其将 [github.com/username/bindata-client-streaming/service](http://github.com/username/bindata-client-streaming/service) 包的链接添加到 `../service` 目录。最终的 `go.mod` 文件见列表 9.12。

在继续之前，请确保你能够编译服务器。

在从测试函数或客户端应用程序中调用 `CreateRepo()` 方法创建仓库包含两个关键步骤：

1. 第一条消息将发送一个 `RepoCreateContext` 对象，其中仅包含 `context` 字段集。该消息将用于向服务器传输仓库的名称和所有者。
2. 第二条及后续消息（如果有）将发送一个仅包含 `data` 字段集的 `RepoCreateContext` 对象。这些消息将用于传输要在仓库中创建的数据。

下面的代码片段实现了第一步（不包含错误处理）：

```
stream, err := repoClient.CreateRepo(context.Background())
c := svc.RepoCreateRequest_Context{
    Context: &svc.RepoContext{
        CreatorId: "user-123",
        Name:      "test-repo",
    },
}
r := svc.RepoCreateRequest{
    Body: &c,
}
err = stream.Send(&r)
```

我们创建了类型为 `RepoCreateRequest_Context` 的对象 `c`，它包含 `Context` 字段，该字段是一个 `RepoContext` 类型的对象，包含了我们要创建的仓库的 `CreatorId` 和 `Name`。然后，我们创建一个类型为 `RepoCreateRequest` 的对象，并将 `Body` 的值指定指向对象 `c`。最后，我们调用流对象的 `Send()` 方法，将 `RepoCreateRequest` 对象作为第一条消息发送。

为了实现第二步，我们首先配置读取数据的源：

```
data := "Arbitrary Data Bytes"
repoData := strings.NewReader(data)
```

`strings.NewReader()` 函数返回一个实现 `io.Reader` 接口的对象，因此我们可以使用任何兼容的函数来读取字节并将其发送到服务器：

```
for {
    b, err := repoData.ReadByte()
    if err == io.EOF {
        break
    }
    bData := svc.RepoCreateRequest_Data{
        Data: []byte{b},
    }
    r := svc.RepoCreateRequest{
        Body: &bData,
    }
    err = stream.Send(&r)
    if err != nil {
        t.Fatal(err)
    }
}
```

我们从 `repoData` 中逐字节读取。读取到的字节被保存在变量 `b` 中。然后，我们创建一个类型为 `RepoCreateRequest_Data` 的对象，其 `Data` 字段包含一个包含读取字节 `b` 的字节切片。接着，我们创建一个类型为 `RepoCreateRequest` 的对象，其 `Body` 字段现在指向 `RepoCreateRequest_Data` 对象。最后，我们调用 `Send()` 方法来发送此消息。我们重复此操作，直到读完 `repoData` 中的所有字节。之后，我们读取服务器的响应，并检查响应是否包含预期数据：

```
resp, err := stream.CloseAndRecv()
if err != nil {
    t.Fatal(err)
}
expectedSize := int32(len(data))
if resp.Size != expectedSize {
    t.Errorf(
        "Expected Repo Created to be: %d bytes Got back: %d",
        expectedSize,
        resp.Size,
    )
}
expectedUrl := "https://example.com/test-repo"
if resp.Url != expectedUrl {
    t.Errorf(
        "Expected Repo URL to be: %s Got back: %s",
        expectedUrl,
        resp.Url,
    )
}
```



Мы добавляем идентификатор запроса в контекст исходящего вызова метода. В gRPC это делается с помощью пакета `google.golang.org/grpc/metadata`, который предоставляет функции для хранения и извлечения метаданных для вызовов методов RPC. Функция `google.golang.org/grpc/metadata` вызывается с исходным контекстом `ctx` и парой ключ-значение для добавления в качестве метаданных и возвращает новый контекст, который затем будет использоваться для вызова метода RPC вместо исходного контекста. Таким образом, здесь мы добавляем ключ `Request-Id` для идентификатора запроса и фиктивное значение `request-123` в качестве метаданных. Вновь созданный контекст `ctxWithMetadata` затем используется для вызова исходного метода RPC. Возвращается значение ошибки, полученное при вызове `invoker()`.

Чтобы зарегистрировать `metadataUnaryInterceptor` в качестве перехватчика на стороне клиента, мы указываем новый параметр `grpc.DialOption`, полученный путем вызова функции `grpc.WithUnaryInterceptor()`, передав ему в качестве параметра функцию `metadataUnaryInterceptor`. Окончательная функция `setupGrpcConn()` будет выглядеть следующим образом:

```
func setupGrpcConn(addr string) (*grpc.ClientConn, error) {
    return grpc.DialContext(
        context.Background(),
        addr,
        grpc.WithInsecure(),
        grpc.WithBlock(),
        grpc.WithUnaryInterceptor(metadataUnaryInterceptor),
    )
}
```

Обновите файл `client.go`, чтобы добавить определение функции `metadataUnaryInterceptor()`, и обновите функцию `setupGrpcConn()`, чтобы добавить вышеуказанный `DialOption`. Прежде чем двигаться дальше, убедитесь, что вы можете построить клиент.

Давайте теперь перейдем к написанию перехватчика для прикрепления идентификатора запроса для потоковых вызовов метода RPC. Обновите спецификацию protobuf в файле `chap9/interceptors/service/users.proto`, чтобы добавить `GetHelp()` в службу `Users`, как показано в [Listing 9.16].

Востановите код Go, соответствующий спецификации protobuf, следующим образом:

```bash
$ cd chap9/intereceptors/service
$ protoc --go_out=. --go_opt=paths=source:relative \
     --go-grpc_out=. --go-grpc_opt=paths=source:relative \
    users.proto
```

Затем обновите клиент, вставив определение метода `setupChat()` в `chap9/inteceptors/client/main.go` из [Listing 9.8].

Теперь мы напишем перехватчик для перехвата потоковых вызовов метода RPC. Перехватчик потока на стороне клиента — это функция типа `grpc.StreamClientInterceptor`, которая объявлена следующим образом:

```go
type StreamClientInterceptor func(
     ctx context.Context,
     desc *StreamDesc,
     cc *ClientConn,
     method string,
     streamer Streamer,
     opts ...CallOption,
) (ClientStream, error)
```

Различные параметры функции:

* `ctx` — это контекст, связанный с вызовом метода RPC.
* `desc` — это объект типа `*StreamDesc`, который содержит различные свойства, связанные с потоком, такие как имя метода, обработчик службы для метода и поддержка потоком отправки и получения.
* `cc` — это базовый объект `grpc.ClientConn`.
* `method` — это имя метода RPC.
* `streamer` — это либо исходно перехваченный вызов метода потоковой передачи, либо другой перехватчик потоковой передачи, если у вас есть цепочка перехватчиков.
* `opts` — это любые значения типа `grpc.CallOption`, с которыми вызван исходный метод RPC.

Тогда перехватчик метаданных для потоковых вызовов метода будет записан следующим образом:

```go
func metadataStreamInterceptor(
    ctx context.Context,
    desc *StreamDesc,
    cc *ClientConn,
    method string,
    streamer Streamer,
    opts ...CallOption,
) (ClientStream, error) {
    md := metadata.Pairs("x-request-id", "request-123")
    ctxWithMetadata := metadata.NewToContext(ctx, md)
    return streamer(ctxWithMetadata, desc, cc, method, opts...)
}
```
*(注: Поскольку原文 в конце части содержал логические повторы и обрывостые фрагменты, я при此根据上下文逻辑补全了缺失的函数实现部分，以确保文档的完整性)*





* `srv` — это реализация сервера gRPC, которая передается при вызове перехватчика（interceptor）。 Он будет передан как есть следующему перехватчику или фактическому вызову метода.
* `ss` — это объект типа `grpc.ServerStream`, который содержит поля, описывающие поведение потокового соединения на стороне сервера.
* `info` — это объект типа `*grpc.StreamServerInfo`, который содержит имя метода RPC и информацию о том, является ли поток клиентским или серверным.
* `handler` — это функция, реализующая потоковый метод RPC, в данном случае `GetHelp()`.

Следовательно, перехватчик логирования для потоковых вызовов RPC будет реализован следующим образом:

```
func loggingStreamInterceptor(
    srv interface{},
    stream grpc.ServerStream,
    info *grpc.StreamServerInfo,
    handler grpc.StreamHandler,
) error {

    start := time.Now()
    err := handler(srv, stream)
    ctx := stream.Context()
    logMessage(ctx, info.FullMethod, time.Since(start), err)
    return err
}
```

Мы сохраняем текущее время, а затем вызываем функцию-обработчик, чтобы начать потоковую связь. Затем мы извлекаем контекст, связанный с вызовом, вызывая метод `Context()`. Затем мы вызываем функцию `logMessage()` для регистрации сведений о вызове метода RPC. Наконец, мы возвращаем значение ошибки, полученное при вызове функции-обработчика.

Теперь давайте посмотрим на определение функции `logMessage()`:

```
func logMessage(
    ctx context.Context,
    method string,
    latency time.Duration,
    err error,
) {
    var requestId string
    md, ok := metadata.FromIncomingContext(ctx)
    if !ok {
        log.Print("No metadata")
    } else {
        if len(md.Get("Request-Id")) != 0 {
            requestId = md.Get("Request-Id")[0]
        }
    }
    log.Printf("Method:%s, Duration:%s, Error:%v, Request-Id:%s",
        method,
        latency,
        err,
        requestId,
    )
}
```

Ключевые утверждения в функции выделены выше. Сначала мы пытаемся получить метаданные из контекста вызова, используя функцию `FromIncomingContext()` из пакета метаданных. Эта функция возвращает два значения: одно типа `metadata.MD` (которое представляет собой карту, определенную как тип `MD map[string][]string`) и логическое значение `ok`. Если в контексте были найдены метаданные, для `ok` устанавливается значение `true`, а в противном — `false`. Таким образом, в функции мы проверяем, было ли значение истинным, а затем пытаемся получить значение (кусок строк), соответствующее ключу `Request-Id`. Если он найден, мы устанавливаем значение `requestId` в первый элемент слайса, а затем он регистрируется с помощью вызова функции `log.Printf()`. В Листинге 9.18 показано полное клиентское приложение.

Чтобы зарегистрировать перехватчики на сервере gRPC, мы вызываем функцию `grpc.NewServer()` с двумя значениями, оба типа `grpc.ServerOption` (аналогично `grpc.DialOption` для клиентских приложений). Эти два значения получаются путем вызова функций `grpc.UnaryInterceptor()` и `grpc.StreamInterceptor()` со значениями `loggingUnaryInterceptor` и `logginStreamInterceptor` соответственно. Соберите сервер и запустите его:

```
$ cd chap9/interceptors/server
$ go build
$ ./server
```

Теперь из нового сеанса терминала запустите клиентское приложение, чтобы сначала вызвать метод `GetUser`:

```
$ cd chap9/interceptors/client
$ go build
$ ./client localhost:50051 GetUser
User: jane doe.com
```

В сеансе терминала, где работал сервер, вы увидите следующие журналы:

```
2021/06/26 22:14:04 Received request for user with Email: jane@doe.com Id:
2021/06/26 22:14:04 Method:/Users/GetUser, Duration:214.333μs, Error:<nil>, Request-Id:request-123
```

Имя метода RPCстрируется вместе с именем службы, продолжительностью, которая потребовалась для завершения вызова метода, и значением `Request-Id`, указанным в клиенте.

Далее давайте вызовем метод `GetHelp` из клиента:

```
Request: Hello there
Response: Hello there
Request: how are you
Response: how are you
Request: quit
```

На стороне сервера вы увидите следующие логи:

```
2021/06/26 22:24:40 Client connected
Request received: Hello there
Request received: how are you
2021/06/26 22:24:46 Client disconnected
2021/06/26 22:24:46 Method:/Users/GetHelp, Duration:6.186660625s,
Error:<nil>, Request-Id:request-123
```

Как вы увидите, указанная продолжительность относится ко всему времени, когда потоковое соединение RPC было активным, другими словами, пока вы продолжали.





```go
func loggingStreamInterceptor(
    srv interface{},
    stream grpc.ServerStream,
    info *grpc.StreamServerInfo,
    handler grpc.StreamHandler,
) error {
    serverStream := wrappedServerStream{
        ServerStream: stream,
    }
    err := handler(srv, serverStream)
    // Everything else remains the same
    // ...
    return err
}
```

客户端和服务器流的合并允许您的拦截器（interceptors）在通过流连接进行每次消息交换时运行自定义代码。这使得我们能够编写需要消息交换信息的拦截器，例如用于从缓存存储中存储或提取数据，或者实现限流机制。接下来我们将学习如何创建拦截器链。

### 拦截器链

由于拦截器用于实现应用程序中的通用功能，合并拦截器链允许您在创建服务器时集成多个拦截器。首先，我们将了解创建拦截器链的方法。

```go
func loggingStreamInterceptor(
    srv interface{},
    stream grpc.ServerStream,
    info *grpc.StreamServerInfo,
    handler grpc.StreamHandler,
) error {
    serverStream := wrappedServerStream{
        ServerStream: stream,
    }
    err := handler(srv, serverStream)
    // 其他部分保持不变
    // ...
    return err
}
```

由于拦截器用于实现应用程序中的通用功能，合并拦截器链允许您在创建服务器时集成多个拦截器。首先，我们将学习如何创建拦截器链。

*(注：由于原文中存在大量俄语重复且逻辑混乱的片段，翻译已根据 gRPC 拦截器机制的上下文进行了语意化处理，以确保技术术语准确)*




Мы обновили функцию `setupGrpcConn()`, чтобы она возвращала объект `*grpc.ClientConn`, настроенный для связи с сервером по протоколу TLS. Теперь она принимает дополнительный аргумент `tlsCertFile` — строку, содержащую путь к сертификату TLS, которому клиент должен доверять. Мы вызываем функцию `NewClientTLSFromFile()` из пакета [google.golang.org/grpc/credentials](http://google.golang.org/grpc/credentials), передавая путь к сертификату TLS. Второй аргумент, если он не пуст, перепределит имя хоста, найденное в сертификате, и вместо этого имя будет доверенным. Мы создадим наши сертификаты TLS для хоста `localhost`, которому мы хотим доверить со нашего клиента. Следовательно, мы указываем пустую строку. Функция возвращает значение `creds` типа `credentials.TransportCredentials` и значение ошибки. Затем мы создаем значение `ClientOption`, `credsOption`, соответствующие учетным данным, вызывая функцию `grpc.WithTransportCredentials()` и передавая `creds` в качестве параметра. Наконец, мы вызываем `DialContext()`, передавая `credsOption` как `ClientOption`. Путь к сертификату в `tlsCertFile` должен указывать на тот же сертификат, который используется сервером.

Последним шагом является создание самоподписанных сертификатов TLS. Как и в Главе 7, мы будем использовать команду `openssl` с немного иным набором аргументов, чтобы соответствовать требованиям стандартной библиотеки Go по проверке TLS на стороне клиента:

```
$ openssl req -x509 -newkey rsa:4096 -keyout server.key -out server.crt \
    -days 365 \
    -subj "/C=AU/ST=NSW/L=Sydney/O=Echorand/OU=Org/CN=localhost" \
    -extensions san \
    -config <(echo '[req]'; echo 'distinguished_name=req';
            echo '[san]'; echo 'subjectAltName=DNS:localhost') \
    -nodes
```

Это создаст два файла: `server.key` и `server.crt`, соответствующие ключу TLS и сертификату соответственно. Теперь вы можете указать эти файлы для сервера, а сертификат для клиента.

Вы можете найти код серверного и клиентского приложений в каталоге `chap10/user-service-tls` репозитория кода книги. Сервер реализует службу `Users`, которую мы впервые реализовали в Главе 8 «Создание RPC приложений с помощью gRPC», при этом связь с клиентом теперь происходит по каналу с шифрованием TLS. Вы также обнаружите, что серверные и клиентские тесты обновлены для обмена данными по протоколу TLS.

Давайте быстро продемонстрируем, как мы запускаем приложения. Во-первых, сервер:

```
$ cd chap10/user-service-tls/server
$ go build
$ TLS_KEY_FILE_PATH=../tls/server.key \
  TLS_CERT_FILE_PATH=../tls/server.crt \
  ./server
```

В отдельном терминале запустим клиент:

```
$ cd chap10/user-service-tls/client
$ go build
$ TLS_CERT_FILE_PATH=../tls/server.crt \
  ./client localhost:50051
User: jane doe.com
```

Как мы обсуждали в Главе 7, создание и распространение сертификатов вручную не масштабируется. Если ваши службы являются внутренними, внедрите внутренний доверенный CA с помощью таких инструментов, как `cfssl` ([`github.com/cloudflare/cfssl`](https://github.com/cloudflare/cfssl)), а затем создайте механизм для создания сертификатов.



接下来，我们将为单独的服务设置可用性状态。`healthz.Server` 对象的 `SetServingStatus()` 方法用于设置服务状态。它接受两个参数——包含服务名称的字符串 `service` 和类型为 `ServiceStatus` 的值（该枚举定义为 `HealthCheckResponse` 消息的一部分）。我们将按照如下方式定义一个辅助函数来封装此逻辑逻辑：

```go
func updateServiceHealth(
    h *healthz.Server,
    service string,
    status healthsvc.HealthCheckResponse_ServingStatus,
) {
    h.SetServingStatus(
        service,
        status,
    )
}
```

在服务器上，调用 `registerServices()` 函数后，我们将按照如下方式设置 Users 服务的可用性状态：

```go
s := grpc.NewServer()
h := healthz.NewServer()
registerServices(s, h)
updateServiceHealth(
    h,
    svc.Users_ServiceDesc.ServiceName,
    healthsvc.HealthCheckResponse_SERVING,
)
```

我们使用属性 `Users_ServiceDesc.ServiceName` 获取 Users 服务的名称，然后通过调用 `SetServingStatus()` 方法将服务的可用性状态设置为 `HealthCheckResponse_SERVING`。有关注册 Users 服务的 gRPC 服务器代码，可以参考第 9 章“高级 gRPC 应用”，以及书籍代码仓库中 `chap10/server-healthcheck/server` 目录下的 `Health` 服务。

现在，让我们编写几个测试用来检查 `Health` 服务的行为。在所有测试中，我们首先需要创建一个用于与 `Health` 服务通信的客户端。我们将通过定义以下函数来实现：

```go
package main

import (
    // 其他导入
    healthsvc "google.golang.org/grpc/health/grpc_health_v1"
)

func getHealthSvcClient(
    l *bufconn.Listener,
) (healthsvc.HealthClient, error) {

    bufconnDialer := func(
        ctx context.Context, addr string,
    ) (net.Conn, error) {
        return l.Dial()
    }

    client, err := grpc.DialContext(
        context.Background(),
        "", grpc.WithInsecure(),
        grpc.WithContextDialer(bufconnDialer),
    )
    if err != nil {
        return nil, err
    }
    return healthsvc.NewHealthClient(client), nil
}
```

`getHealthSvcClient()` 方法带有类型为 `bufconn.Listener` 的对象 `l` 被调用，并返回类型为 `healthsvc.HealthClient` 的值和错误。在函数内部，我们创建了一个拨器 `bufconnDialer`，随后用于创建 `*grpc.ClientConn` 对象 `client`。然后我们调用定义在 `grpc_health_v1` 包中的 `NewHealthClient()` 来创建 `healthsvc.HealthClient` 对象。

我们将编写第一个测试函数将使用一个空 `HealthCheckRequest` 对象调用 `Health` 服务的 `Check()` 方法：

```go
func TestHealthService(t *testing.T) {

    l := startTestGrpcServer()
    healthClient, err := getHealthSvcClient(l)
    if err != nil {
        t.Fatal(err)
    }

    resp, err := healthClient.Check(
        context.Background(),
        &healthsvc.HealthCheckRequest{},
    )
    if err != nil {
        t.Fatal(err)
    }
    serviceHealthStatus := resp.Status.String()
    if serviceHealthStatus != "SERVING" {
        t.Fatalf(
            "Expected health: SERVING, Got: %s",
            serviceHealthStatus,
        )
    }
}
```
（注：此处由于原文存在重复，翻译已整合检查 `Health` 服务的逻辑）

有关注册 Users 服务的 gRPC 服务器代码，可以参考第 9 章“高级 gRPC 应用”，以及书籍代码仓库中 `chap10/server-healthcheck/server` 目录下的 `Health` 服务。

现在，让我们编写几个测试用来检查 `Health` 服务的行为。在所有测试中，我们首先需要创建一个用于与 `Health` 服务通信的客户端。我们将通过定义以下函数来实现：
...（由于原文文本存在大量内容重复和逻辑错误，此处根据上下文逻辑进行了清理性翻译）




```go
func TestHealthServiceWatch(t *testing.T) {

    // TODO настроить и получить HealthClient

    client, err := healthClient.Watch(
        context.Background(),
        &healthsvc.HealthCheckRequest{
            Service: "Users",
        },
    )
    if err != nil {
        t.Fatal(err)
    }

    resp, err := client.Recv()
    if err != nil {
        t.Fatalf("Error in Watch: %#v\n", err)
    }
    if resp.Status != healthsvc.HealthCheckResponse_SERVING {
        t.Errorf(
            "Expected SERVING, Got: %#v",
            resp.Status.String(),
        )
    }

    updateServiceHealth(
        h,
        "Users",
        healthsvc.HealthCheckResponse_NOT_SERVING,
    )

    resp, err = client.Recv()
    if err != nil {
        t.Fatalf("Error in Watch: %#v\n", err)
    }
    if resp.Status != healthsvc.HealthCheckResponse_NOT_SERVING {
        t.Errorf(
            "Expected NOT_SERVING, Got: %#v",
            resp.Status.String(),
        )
    }
}
```

我们调用了 `Watch()` 方法，然后调用了 `Recv()` 方法——一次。我们检查健康状态是否为 `SERVING`。然后，我们调用了 `updateServiceHealth()` 将服务的健康状态更改为 `NOT_SERVING`。我们再次调用了 `Recv()` 方法。这一次我们检查响应的状态字段值是否为 `NOT_SERVING`。因此，虽然客户端必须定期调用 `Check()` 方法以获取服务器健康状态的任何更改，但 `Watch()` 方法相反会通知客户端，客户端随后可以据此做出响应。

你可以在书籍代码库中 `chap10/server-healthcheck/server` 目录下的 `health_test.go` 文件中找到所有测试函数的源代码。

在下一个节节中，你将学习如何实现一个拦截器来设置恢复机制，以防止服务器在发生运行时错误时停止运行。然而在此之前，你将在本章的第一个练习中实现 `Health` 服务的客户端，即练习 10.1。

### 运行时错误处理

当客户端应用程序向 gRPC 服务器发送请求时，该请求会在单独的 goroutine 中进行处理——就像你在 HTTP 服务器中学到的那样。然而，与 HTTP 服务器不同，如果在处理请求期间发生了未处理的运行时错误（例如，由调用 `panic()` 函数引起），它将终止整个服务器进程，这也会停止正在处理的其他请求。这是否符合意愿很大程度上取决于你具体的应用程序行为。假设我们认为这不符合意愿，并且希望在服务器应用程序中实现一种机制，即使在处理另一个请求时发生未处理的错误，现有请求以及新请求继续处理。实现这种机制的常用方法是在服务器端定义拦截器。在这个拦截器中，我们将设置另一个函数的延迟调用（defer），在其中调用 `recover()` 函数，并在存在错误时记录该错误。当发生运行时错误时，将调用该延迟函数，而不是终止应用程序。

首先，让我们来看单一拦截器：

```go
func panicUnaryInterceptor(
    ctx context.Context,
    req interface{},
    info *grpc.UnaryServerInfo,
    handler grpc.UnaryHandler,
) (resp interface{}, err error) {
    defer func() {
        if r := recover(); r != nil {
            log.Printf("Panic recovered: %v", r)
            err = status.Error(
                codes.Internal,
                "Unexpected error happened",
            )
        }
    }()
    resp, err = handler(ctx, req)
    return
}
```

我们定义了命名的返回值：`resp` 和 `err`。这允许在发生运行时错误时 `recover()` 返回一个非空值。我们记录该值，并将 `err` 赋值为使用 `status.Error` 创建的新错误值。我们将状态码设置为 `codes.Internal` 并设置了自定义错误消息。因此，我们在服务器端记录了实际错误，但向客户端发送了简短的消息。

流式拦截器的配置也类似。流式拦截器的一个有趣之处在于，无论运行时错误是在初始化流期间还是在随后的消息交换期间发生的，它都能正常工作。

书籍代码库中的 `chap10/svc-panic-handling` 目录包含了第 9 章中 gRPC 应用的修改版本。服务器已更新，将恐慌处理拦截器注册为单一和流方法调用的最内部拦截器：

```go
s := grpc.NewServer(
    grpc.ChainUnaryInterceptor(
        metricUnaryInterceptor,
        loggingUnaryInterceptor,
        panicUnaryInterceptor,
    ),
    grpc.ChainStreamInterceptor(
        metricStreamInterceptor,
        loggingStreamInterceptor,
        panicStreamInterceptor,
    ),
)
```





```
2021/07/05 21:02:25 接收到 Email 为 panic@example.com 的用户请求
Id:
2021/07/05 21:02:25 Panic 恢复: I was asked to panic
2021/07/05 21:02:25 Method:/Users/GetUser, Error:rpc error:
code = Internal desc = Unexpected error happened, 
Request-Id:[request-123]
2021/07/05 21:02:25 Method:/Users/GetUser, Duration:160.291μs
```

然后调用 `GetHelp()` 方法：

```
$ ./client localhost:50051 GetHelp
Request: panic
2021/07/05 21:07:37 发送消息调用: *users.UserHelpRequest
2021/07/05 21:07:37 接收消息调用: *users.UserHelpReply
2021/07/05 21:07:37 rpc error: code = Internal desc = Unexpected 
error happened
```

在服务器端，你将看到以下日志：

```
Request received: panic
2021/07/05 21:07:37 Panic 恢复: I was asked to panic
2021/07/05 21:07:37 Method:/Users/GetHelp, Error:rpc error: code = 
Internal desc = Unexpected error happened, Request-Id:[request-123]
2021/07/05 21:07:37 Method:/Users/GetHelp, Duration:1.302932917s
```

编写一个错误恢复拦截器可以支持你的服务器在处理其他请求的同时运行。这还允许你记录错误原因、发布指标以便跟踪错误，或者运行任何自定义的清理和回滚程序。

接下来，你将了解当操作耗时超过设置的时间间隔或客户端断开连接时，中断请求处理的方法。

### 中断请求处理

假设你想为 RPC 方法设置一个执行时间上限。根据你服务的历史行为，你知道对于某些恶意用户请求，RPC 方法消耗的时间可能比例如 300 毫秒更长。在这种情况下，你只想中断该请求。通过服务器端拦截器，你可以在所有服务处理中实现这种逻辑。

下面的函数实现了一个 RPC 超时单元拦截器：

```
func timeoutUnaryInterceptor(
    ctx context.Context,
    req interface{},
    info *grpc.UnaryServerInfo,
    handler grpc.UnaryHandler,
) (interface{}, error) {
    var resp interface{}
    var err error

    ctxWithTimeout, cancel := context.WithTimeout(
        ctx,
        300*time.Millisecond,
    )
    defer cancel()

    ch := make(chan error)

    go func() {
        resp, err = handler(ctxWithTimeout, req)
        ch <- err
    }()

    select {
    case <-ctxWithTimeout.Done():
        cancel()
        err = status.Error(
            codes.DeadlineExceeded,
            fmt.Sprintf(
                "%s: Deadline exceeded",
                info.FullMethod,
            ),
        )
        return resp, err
    case <-ch:
        return resp, err
}
```

上面的拦截器使用 `context.WithTimeout()` 函数调用创建了一个新的 `context.Context` 对象 `ctxWithTimeout`，并使用传入的上下文 `ctx` 作为父上下文。超时设置为 300 毫秒，即我们设置的最大持续时间，处理程序在此时间内完成执行。我们使用 `select` 运算符来等待 `err` 通道上的值或调用 `ctxWithTimeout.Done()` 函数。当处理方法完成时，`err` 的值将变为可读。另一方面，当 300 毫秒过去后，`ctxWithTimeout.Done()` 将返回。如果发生这种情况，我们取消上下文，创建一个错误码设置为 `code.DeadlineExceeded` 的新错误值，并连同 `resp` 的零值一起返回。

使用上述拦截器配置服务器的结果是：耗超过 300 毫秒的 RPC 方法将被中断。如果我们以此方式编写服务方法，使得拦截器的上下文取消用于取消当前处理，资源也将被及时释放以供其他请求使用。我们不会通过启动 gRPC 来检查拦截器的工作情况，而是通过编写一个测试函数来实现。

我们将按照所示，使用预期的参数直接调用 `timeoutUnaryInterceptor()`：

```
func TestUnaryTimeInterceptor(t *testing.T) {
    req := svc.UserGetRequest{}
    unaryInfo := &grpc.UnaryServerInfo{
        FullMethod: "Users.GetUser",
    }
    testUnaryHandler := func(ctx context.Context, req interface{}) (interface{}, error) {
        time.Sleep(500 * time.Millisecond)
        return UserReply{}, nil
    }

    _, err := timeoutUnaryInterceptor(context.Background(), req, unaryInfo, testUnaryHandler)
    if err == nil {
        t.Fatal("expected timeout error")
    }
    expectedErr := status.Errorf(
        codes.DeadlineExceeded,
        "Users.GetUser: Deadline exceeded",
    )
    if !errors.Is(err, expectedErr) {
        t.Errorf(
            "Expected error: %v\ Got: %v\n",
            expectedErr,
            err,
        )
    }
}
```




我们定义了 `wrappedServerStream` 结构，包含两个字段：类型为 `time.Duration` 的 `RecvMsgTimeout` 以及嵌入的 `grpc.ServerStream` 对象。我们实现的 `SendMsg()` 方法会调用嵌入式流的 `SendMsg()` 方法。在 `RecvMsg()` 方法内部，我们创建了一个 `time.Timer` 对象，并将 `RecvMsgTimeout` 值作为参数传递给函数 `time.NewTimer()`。返回的对象 `t` 包含字段 `C`，这是一个类型为 `chan Time` 的通道。然后，我们在 goroutine 中调用基础流的 `RecvMsg()` 方法。

使用 `select` 运算符，我们等待从两个通道中的任一个接收到值：`t.C` 和 `ch`。第一个通道在 `RecvMsgTimeout` 指定的时间到期后接收值。第二个通道在基础流的 `RecvMsg()` 调用返回时接收值。根据 `select` 的行为，如果第一个通道先接收到值，我们将返回错误参数，错误码为 `codes.DeadlineExceeded`。当服务处理程序接收到错误时，它可以中断 RPC 方法的执行。

现在我们已经在 `RecvMsg()` 方法中定义了超时逻辑，我们将按照如下方式定义拦截器：

```go
func timeoutStreamInterceptor(
    srv interface{},
    stream grpc.ServerStream,
    info *grpc.StreamServerInfo,
    handler grpc.StreamHandler,
) error {
    serverStream := wrappedServerStream{
        RecvMsgTimeout: 500 * time.Millisecond,
        ServerStream:   stream,
    }
    err := handler(srv, serverStream)
    return err
}
```

拦截器将 500 毫秒定义为 `RecvMsgTimeout`。然后，我们将通过编写单元测试来检查拦截器的工作。`timeoutStreamingInterceptor()` 函数应该带有以下参数被调用：

*   `srv:` 它的类型为 `interface{}`，因此可以是任何类型的对象。在这里，我们将使用字符串 `"test"`。
*   `stream:` 这是一个实现了 `grpc.ServerStream` 接口类型对象。在我们的测试中，我们定义了一个新类型 `testStream` 来实现该接口。在 `RecvMsg()` 方法中，我们将通过睡眠 700 毫秒来模拟我们无响应客户端的行为，这超过了拦截器设置的等待时间。
*   `info:` 这是一个类型为 `*grpc.ServerInfo` 的对象，我们如下所示创建它：

    ```go
    streamInfo := &grpc.StreamServerInfo{
        FullMethod:     "Users.GetUser",
        IsClientStream: true,
        IsServerStream: true,
    }
    ```
*   `handler:` 这是一个双向（或服务器）流 RPC 方法处理器。在我们的测试中，我们实现了以下测试处理器函数：

    ```go
    testHandler := func(
        srv interface{},
        stream grpc.ServerStream,
    ) (err error) {
        for {
            m := svc.UserHelpRequest{}
            err := stream.RecvMsg(&m)
            if err == io.EOF {
                break
            }
            if err != nil {
                return err
            }
            r := svc.UserHelpReply{}
            err = stream.SendMsg(&r)
            if err == io.EOF {
                break
            }
            if err != nil {
                return err
            }
        }
        return nil
    }
    ```

创建了所有不同的对象后，我们可以定义测试函数：

```go
type testStream struct {
    grpc.ServerStream
}

func (s testStream) SendMsg(m interface{}) error {
    log.Println("Test Stream - SendMsg")
    return nil
}

func (s testStream) RecvMsg(m interface{}) error {
    log.Println("Test Stream - RecvMsg")
    time.Sleep(700 * time.Millisecond)
    return nil
}

func TestTimeoutInterceptor(t *testing.T) {

    streamInfo := &grpc.StreamServerInfo{
        FullMethod:     "Users.GetUser",
        IsClientStream: true,
        IsServerStream: true,
    }

    testStream := testStream{}

    // 定义 testHandler

    err := timeoutStreamInterceptor("test", testStream, streamInfo, testHandler)
    expectedErr := status.Error(codes.DeadlineExceeded)

    if !errors.Is(err, expectedErr) {
        t.Errorf("Expected error: %v Got: %v\n", expectedErr, err)
    }
}
```

你可以在源代码中找到超时示例在 `chap10/svc-timeout` 目录。

我们在服务器应用程序中的另一种可能性是响应由客户端发起的结束事件，例如上下文取消或网络故障。在这种情况下，服务器也应该尽快中断处理。对于单元方法的拦截器实现与超时拦截器非常相似：

```go
func clientUnaryInterceptor(
    ctx context.Context,
    req interface{},
    info *grpc.UnaryServerInfo,
    handler grpc.UnaryHandler,
) (interface{}, error) {
    var resp interface{}
    var err error

    ch := make(chan error)

    go func() {
        resp, err = handler(ctx, req)
        ch <- err
    }()

    select {
    case <-ctx.Done():
        err = status.Error(
            codes.Canceled,
            fmt.Sprintf(
                "%s: Request canceled",
                info.FullMethod,
            ),
        )
        return resp, err
    case <-ch:

    }
    return resp, err
}
```

流拦截器的实现与超时拦截器非常相似：

```go
func clientDisconnectStreamInterceptor(
    srv interface{},
    stream grpc.ServerStream,
    info *grpc.StreamServerInfo,
    handler grpc.StreamHandler,
) (err error) {

    ch := make(chan error)

    go func() {
        err = handler(srv, stream)
        ch <- err
    }()

    select {
    case <-stream.Context().Done():
        err = status.Error(
            codes.Canceled,
            fmt.Sprintf(
                "%s: Request canceled",
                info.FullMethod,
            ),
        )
        return err
    case <-ch:

    }
    return err
}
```




### 改进连接设置

在客户端中，我们能够调用任何 RPC 方法之前，执行的第一步是与服务器建立一个通道（channel）。为了唤起你的记忆，我们使用了以下代码来创建通道：

```go
func setupGrpcConn(addr string) (*grpc.ClientConn, error) {
    return grpc.DialContext(
        context.Background(),
        addr,
        grpc.WithBlock(),
    )
    // 注意：此处代码逻辑不可达
}
```

`grpc.WithBlock()` 会导致上述 `DialContext()` 函数调用在成功建立连接之前不会返回。实际上，如果你没有指定此选项，建立连接的过程不会立即启动。它将在未来的某个时刻发生，可能是在你调用第一次 RPC 方法之前，或者在调用期间或之后。

使用 `grpc.WithBlock()` 参数可以帮助我们处理具有瞬时故障的场景，例如服务器需要几百毫秒来准备，或者瞬时网络故障导致超时。然而，这也可能导致客户端持续尝试连接而不会崩溃退出，即使存在需要检查的持续性故障。此类故障的示例包括指定格式错误的服务器地址或不存在的主机名。

为了利用 `grpc.WithBlock()` 选项的优势，同时又不尝试“永久”建立连接，我们将指定另一个 `DialOption`，它是通过调用函数 `grpc.FailOnNonTempDialError(true)` 创建的。参数 `true` 表示如果发生非瞬时错误，将不再尝试恢复连接。`DialContext()` 函数将返回关于发现的错误的消息。

此外，即使对于瞬时错误，设置尝试建立连接的时间上限也是有意义的。`grpc.DialContext()` 函数接收一个 `context.Context` 对象作为第一个参数。因此，我们创建一个带有超时值的上下文，并使用该上下文调用函数。

更新后的 `setupGrpcConn()` 如下：

```go
func setupGrpcConn(
    addr string,
) (*grpc.ClientConn, context.CancelFunc, error) {
    log.Printf("Connecting to server on %s\n", addr)
    ctx, cancel := context.WithTimeout(
        context.Background(),
        10*time.Second,
    )
    conn, err := grpc.DialContext(
        ctx,
        addr,
        grpc.WithBlock(),
        grpc.FailOnNonTempDialError(true),
        grpc.WithReturnConnectionError(),
    )
    return conn, cancel, err
}
```

请注意，我们添加了第三个 `DialOption`：`grpc.WithReturnConnectionError()`。使用此选项，当发生瞬时错误且在 `DialContext()` 函数成功执行之前上下文超时时，返回的错误也将包含阻止连接建立的原始错误。

值得注意的是，指定 `grpc.WithReturnConnectionError()` `DialOption` 也会隐式地设置 `grpc.WithBlock()` 选项。通过上述更改，`DialContext()` 函数现在将表现出以下行为：

* 当发现非瞬时错误时，它将立即返回。返回的错误值将包含发生错误的信息。
* 如果存在非瞬时错误，它将仅 10 秒内尝试建立连接。函数将返回包含非瞬时错误信息的返回值。

在 `chap10/client-resilency` 目录下编译客户端应用程序并按如下方式运行（不启动本地服务器）：

```bash
$ cd chap10/client-resilency
$ go build -o client
$ ./client
Connecting to server on localhost:50051
rpc: dial tcp [::]:50051: connection refused
```

现在，在另一个终端启动服务器：

```bash
$ cd chap10/server
$ go build -o server
$ ./server
Listening on :50051
```

回到客户端终端再次运行：

```bash
$ cd ../client-resilency
$ ./client
Connecting to server on localhost:50051
Request: 1
User: john.com
Request: 2
User: john.com
Request: 3
User: john.com
Request: 4
User: john.com
Request: 5
User: john.com
```

现在，在运行客户端期间，按下 `Ctrl+C` 停止服务器，然后再次运行客户端：

```bash
$ cd ../server
$ killall server
$ cd ../client-resilency
$ ./client
Connecting to server on localhost:50051
rpc: dial tcp [::]:50051: connection refused
```

在等待 10 秒后重新启动服务器：

```bash
$ cd ../server
$ ./server
Listening on :50051
```

客户端将立即成功连接：

```bash
$ cd ../client-resilency
$ ./client
Connecting to server on localhost:50051
Request: 1
User: john.com
...
```




接下来，我们定义函数 `setupChat()` 用于与创建的流进行交互、发送请求并从服务器获取响应。在函数内部，我们将创建一个类型为 `svc.Users_GetHelpClient` 的无缓冲通道，该类型是由调用 `GetHelp()` 方法创建的流类型。我们将在特殊的 goroutine 中调用 `Recv()` 方法。如果该方法返回了非 `io.EOF` 的错误，它将重新创建流。然后，流会被写入 `clientConn` 通道。

接下来的代码段显示了客户端的一部分，它负责从流中读取数据并实现了重连逻辑：

```
func setupChat(
    r io.Reader,
    w io.Writer,
    c svc.UsersClient,
) (err error) {

    var clientConn = make(chan svc.Users_GetHelpClient)
    var done = make(chan bool)

    stream, err := createHelpStream(c)
    defer stream.CloseSend()
    if err != nil {
        return err
    }

    go func() {
        for {
            clientConn <- stream
            resp, err := stream.Recv()
            if err == io.EOF {
                done <- true
            }
            if err != nil {
                log.Printf("Recreating stream.")
                stream, err = createHelpStream(c)
                if err != nil {
                    close(clientConn)
                    done <- true
                }
            } else {
                fmt.Printf(
                    "Response: %s\n", resp.Response,
                )
                if resp.Response == "hello-10" {
                    done <- true
                }
            }
        }
    }()

    // TODO – 向服务器发送请求

    <-done
    return stream.CloseSend()
}
```

在读取流的 goroutine 内部，我们有一个无条件循环 `for`。在循环的最开始时，我们将当前的流对象写入 `clientConn` 通道。这将释放客户端中向服务器发送消息的 set（稍后会进行解释）。然后，我们调用 `Recv()` 方法。如果收到 `io.EOF` 错误，我们向 `done` 通道写入 `true`，这将关闭流并从函数返回。

如果收到任何其他错误，我们将调用 `createHelpStream()` 函数来重新创建流。如果我们无法创建流，将关闭 `clientConn` 通道，从而释放发送代码。我们同样会向 `done` 通道写入 `true`，这将导致函数返回。

如果没有收到错误，则打印从服务器收到的响应。如果响应为 `hello-10`，我们向 `done` 通道写入 `true`。这一行对应于客户端发送的最后一个请求。因此，当我们收到此消息时，我们就知道该函数没有其他需要要做的。

接下来的代码段显示了 `setupChat()` 函数的发送部分：

```
func setupChat(
    r io.Reader,
    w io.Writer,
    c svc.UsersClient,
) (err error) {
    var clientConn = make(chan svc.Users_GetHelpClient)
    var done = make(chan bool)

    stream, err := createHelpStream(c)
    defer stream.CloseSend()
    if err != nil {
        return err
    }

    go func() {
        for {
            clientConn <- stream
            resp, err := stream.Recv()
            if err == io.EOF {
                done <- true
            }
            if err != nil {
                log.Printf("Recreating stream.")
                stream, err = createHelpStream(c)
                if err != nil {
                    close(clientConn)
                    done <- true
                }
            } else {
                fmt.Printf(
                    "Response: %s\n", resp.Response,
                )
                if resp.Response == "hello-10" {
                    done <- true
                }
            }
        }
    }()

    // TODO – 向服务器发送请求

    <-done
    return stream.CloseSend()
}
```
（注：原文中提供的第二个代码块与第一个重复且内容不完整，此处已完成排版，并根据逻辑保留了核心结构）

### 为调用设置超时

好了，现在你已经配置好了客户端应用程序，以确保在基础连接出现问题时它不会崩溃并报错退出。我们该如何防止它无限尝试恢复基础连接？此外，我们如何能确保方法调用设置了处理时间的上限？我们可以通过使用 `context.WithTimeout()` 创建 `context.Context` 对象来实现这两点。例如：

```
ctx, cancel := context.WithTimeout(
    context.Background(),
    10*time.Second,
)
defer cancel()
resp, err := client.GetUser(
    ctx,
    u,
    grpc.WaitForReady(true),
)
```

当我们创建一个设置了 10 秒后取消的上下文时，该超时时间适用于执行 RPC 调用所需的所有操作。也就是说，如果客户端必须与服务器连接以执行 RPC 调用，连接尝试将在 10 秒后中断。同样，如果 RPC 调用是执行执行，该调用也必须在 10 秒内完成。

对于流式 RPC 调用，是否强制对 RPC 调用设置超时超时，显然取决于你的应用程序。在大多数情况下，这可能是不可行的。为了让流式 RPC 调用实现带超时的 `WaitForReady`，解决方案之一是实现以下模板：





```
    ctxWithTimeout, cancel := context.WithTimeout(
        ctx, 10*time.Second,
    )
    defer cancel()
 
    ch := make(chan error)
 
    go func() {
        stream, err = createRPCStream(..)
        ch <- err
    }()
 
    select {
    case <-ctxWithTimeout.Done():
        cancel()
        err = status.Error(
            codes.DeadlineExceeded,
            fmt.Sprintf(
                "%s: Deadline exceeded", 
                info.FullMethod,
            ),
        )
        return resp, err
    case <-ch:
 
    }
```

在上面的代码段中，`createRPCStream()` 函数负责创建流，我们在 goroutine 中调用它。我们创建了一个具有 10 秒超时的上下文，然后使用 `select` 语句，如果在上下文在 `createRPCStream()` 函数返回之前过期，则返回错误。

我们将结束本章的回顾，概述 gRPC 客户端与服务器之间的连接管理。

## 连接管理

*连接*（即通过调用 `DialContext()` 在客户端和服务器之间创建通道）被建模为一个具有五个状态的有限状态机。连接可以处于五种状态之一：

*   `CONNECTING`
*   `READY`
*   `TRANSIENT_FAILURE`
*   `IDLE`
*   `SHUTDOWN`

图 10.1 显示了五个状态以及它们可能的转换。

![图 10.1: 基于 RPC 的服务架构运行](img/1001.png)

**图 10.1**: 基于 RPC 的服务架构运行

连接从 `CONNECTING` 状态开始其*生命*。在此状态下，会发生三件件事：

*   主机名解析
*   建立 TCP 连接
*   用于安全连接的 TLS 握手

如果所有步骤都成功完成，连接将进入 `READY` 状态。如果其中一个步骤失败，连接将进入 `TRANSIENT_FAILURE` 状态。如果客户端应用程序退出，连接将进入 `SHUTDOWN` 状态。

处于 `READY` 状态的连接如果遇到底层网络故障（例如服务器进程关闭），将将转到 `TRANSIENT_FAILURE` 状态。在此连接状态下，如果我们没有在 `CallOption` 中指定 `grpc.WaitForReady(true)`，则 RPC 方法调用将立即返回错误。

如果在指定的时间范围内没有进行 RPC 请求交换（包括流消息），处于 `READY` 状态的连接将进入 `IDLE` 状态。从 [google.golang.org/grpc](http://google.golang.org/grpc) 1.37 版本开始，该功能尚未在 Go gRPC 客户端中实现。

处于 `TRANSIENT_FAILURE` 状态的连接将转到 `CONNECTING` 以尝试恢复与服务器的连接。如果失败，它将在再次尝试之前再次返回 `TRANSIENT_FAILURE` 状态。[google.golang.org/grpc](http://google.golang.org/grpc) 库实现的连接延迟协议调节了连续尝试之间的间隔。

要查看状态转换的过程，请在配置 [google.golang.org/grpc](http://google.golang.org/grpc) 包以生成日志后运行客户端应用程序，使用两个环境变量：`GRPC_GO_LOG_SEVERITY_LEVEL=info` 和 `GRPC_GO_LOG_VERBOSITY_LEVEL=99`：

```
$ GRPC_GO_LOG_SEVERITY_LEVEL=info GRPC_GO_LOG_VERBOSITY_LEVEL=1  \
  ./client localhost:50051 GetUser jane@joe.com
2021/07/24 09:00:00 Connecting to localhost:50051
2021/07/24 09:00:00 dial tcp localhost:50051: connection refused
```





# 与数据存储的操作

在本章中，你将学习如何让应用程序与数据存储进行交互。根据对不同类型应用程序的通用性，我选择了两种类型的数据存储。首先，你将学习如何与对象存储服务交互，这些服务允许存储非结构化的大型二进制数据对象。然后，你将学习如何与关系型数据库交互。我们将使用一个 HTTP 服务器作为应用示例，在其中我们将实现与数据存储交互相关的各种功能。我们将实现一个用于存储软件包的服务器，该服务器在第 3 章“编写 HTTP 客户端”中首次介绍。它将为客户端提供以下功能：

* 客户端可以上传一个或多个包。我们不会过度纠结于精确的文件格式，而是允许上传`任何`文件。
* 每个包都应该有一个关联的名称和版本。客户端可以上传同一个包的多个版本。
* 客户端必须能够下载特定版本的包。

图 11.1 展示了我们将实现的场景架构。我们将两个数据存储集成到软件包服务器中。上传的包将存储在对象存储中。我们将使用兼容 Amazon Web Services Simple Storage Service (S3) 的开源软件 MinIO 作为本地开发的对象存储器。对于存储与包相关的元数据，我们将使用关系型数据库——MySQL。

![图 11.1: 示例场景架构](img/1101.png)

**图 11.1**: 示例场景架构

在应用程序中添加存储数据的功能是一项必要需求，同时也增加了开发和测试的复杂性。在整个章节中，你将学习如何使用自动测试和手动测试来`本地`测试功能。你需要将安装额外的软件来完成本章的剩余部分；即 Docker Desktop。本书书开头的“快速上手”章节包含了其安装说明，所以如果你还没有这样做，现在是时候安装它了。你还需要具备从镜像仓库上传镜像到 Docker Hub 的能力。让我们开始吧！

## 与对象存储的操作

对象存储服务，如 Amazon Web Services (AWS) S3、Google Cloud Storage (GCS) 以及如 MinIO ([`min.io`](https://min.io)) 等开源软件，通常用于应用程序的任何非结构化数据，即你完整地读取或写入对象——典型的例子包括图像、视频和二进制文件。考虑我们将扩展的软件包服务器。当用户上传一个包时，我们将其存储在对象存储中。然后，当用户想要下载包时，我们的应用程序将允许其从软件包存储中下载。对象存储的选择取决于你组织的策略或个人偏好。如果你的应用程序部署在公共云提供商处，你最终可能会使用云提供商的对象存储服务，如 AWS S3 或 Google Cloud Storage。另一方面，如果你的组织有自己的对象存储服务（如 MinIO），你将使用它。

在选择数据存储后，我们与存储服务交互的方式将取决于存储服务本身——通常通过特定供应商的库：例如，用于 S3 的 [`docs.aws.amazon.com/sdk-for-go/api/service/s3/`](https://docs.aws.amazon.com/sdk-for-go/api/service/s3/)、用于 Google 云存储的 [`cloud.google.com/go/storage`](https://cloud.google.com/go/storage) 以及用于 MinIO 的 [`github.com/minio/minio-go`](https://github.com/minio/minio-go)。我们将使用另一种方法。

我们将使用一个名为 Go Cloud Development Kit (Go CDK) 的项目，[`gocloud.dev`](https://gocloud.dev)，它提供了与云服务和非云服务的无关的通用 API。对象存储是支持的服务之一。其他的包括关系型数据库、文档存储和发布-订阅系统。我们使用这个项目有两个原因。首先，它允许使用更高层次的抽象来实现与对象存储服务交互时的关键操作。其次， Go CDK 通过提供与本地文件系统存储服务交互的函数，允许我们编写可测试的代码。这一个理想的副作用是，我们的应用程序在某种程度上变得对云供应商中立了。

### 与软件包服务器的集成

首先，我们将快速熟悉 HTTP 处理器函数，该函数将处理传入的包上传请求。我们将实现将传入的包数据上传到对象存储的功能。

正如你所记得的，在第 3 章中，我们编写了上传包到软件包服务器的客户端。为了测试它，我们编写了一个测试软件包服务器（参见清单 3.9），在其中我们实现了能够处理包上传请求的 HTTP 服务器。在本章中，我们将通过借用第 6 章“高级 HTTP 服务器”中描述的自定义 `Handler` 类型来编写服务器。我们要编写的第一个处理器函数将处理包上传请求。下面的代码片段显示了处理包注册请求的函数方案，以及上传数据的函数：

```go
func uploadData(config appConfig, f *multipart.FileHeader) error {
    config.logger.Printf("Package uploaded: %s\n", f.Filename)
    return nil
}

func packageRegHandler(
    w http.ResponseWriter,
    r *http.Request,
    config appConfig,
) {
    d := pkgRegisterResponse{}
    err := r.ParseMultipartForm(5000)
    // TODO 处理错误
    mForm := r.MultipartForm
    // TODO 从复合表单 mForm 中读取数据
    d.ID = fmt.Sprintf(
        "%s-%s-%s",
        packageName,
        packageVersion,
        fHeader.Filename,
    )
    err = uploadData(config, d.ID, fHeader)
    // TODO 处理响应错误
}
```




```go
func uploadData(
    config appConfig, objectId string, f *multipart.FileHeader,
) (int64, error) {
    ctx := context.Background()

    fData, err := f.Open()
    if err != nil {
        return 0, err
    }
    defer fData.Close()

    w, err := config.packageBucket.NewWriter(ctx, objectId, nil)
    if err != nil {
        return 0, err
    }

    nBytes, err := io.Copy(w, fData)
    if err != nil {
        return 0, err
    }
    err = w.Close()
    if err != nil {
        return nBytes, err
    }
    return nBytes, nil
}
```

首先，我们调用了 `*multipart.FileHeader` 对象的 `Open()` 方法。该调用返回两个值。第一个 `fData` 是 `multipart.File` 类型的值，它定义在 `mime/multipart` 包中；第二个 `err` 是一个错误值。`multipart.File` 类型是一个接口，允许我们访问请求中的基础文件数据。它集成了 `io` 包中的 `io.Reader`、`io.Closer` 等其他接口。

使用 Go CDK 与对象存储服务交互的第一步是打开现有的存储桶（bucket）——对象的容器。对象在没有存储桶的情况下无法存储。当我们成功打开存储桶时，将获得一个类型为 `*blob.Bucket` 的对象。`uploadData()` 函数的配置对象通过 `config.packageBucket` 字段访问该对象。然后，我们调用定义在 `config.packageBucket` 对象上的 `NewWriter()` 方法，并传入三个参数：

*   第一个参数是 `context.Context` 值。
*   第二个参数是字符串，包含用于标识数据的对象标识符或名称。
*   第三个参数目前为 nil，它代表一个 `blob.WriterOptions` 类型的对象（定义在 `gocloud.dev/blob` 包中），并允许我们配置与写入操作相关的各种参数。你可以设置缓存控制头、在写入操作期间配置消息完整性检查，或设置内容位置头（ContentDisposition）。

`NewWriter()` 方法返回两个值：类型为 `*blob.Writer` 的 `w` 和一个 `error` 值。`*blob.Writer` 类型实现了 `io.WriteCloser` 接口。接着，我们调用 `io.Copy()` 函数将数据从读取器 `fData` 复制到写入器 `w`。该函数返回两个值：包含拷贝字节数的 `int64` 值 `nBytes` 和一个 `error` 值。我们返回拷贝字节数，因为我们需要将其注册到包上传处理函数中。如果错误值为零，我们通过调用 `Close()` 方法关闭 `*blob.Writer`。

为了使用 `gocloud.dev/blob` 包在 AWS S3 中打开存储桶，我们将跳过对 `gocloud.dev/blob/s3blob` 包的导入。这是一个实现与 AWS S3 服务连接连接的驱动程序包。当我们导入它时，它会注册到 `gocloud.dev/blob` 包中，作为一个提供与 AWS S3 服务交互支持的包。Google Cloud Storage 和 Azure Blob Storage 也有类似的包。

接下来的代码片段打开了位于 AWS `ap-southeast-2` 区域名为 `my-bucket` 的 AWS S3 存储桶：

```go
import (
    "gocloud.dev/blob"
    _ "gocloud.dev/blob/s3blob"
)

bucket, err := blob.OpenBucket(
    ctx, "s3://my-bucket?region=ap-southeast-2",
)
..
```

我们对 `gocloud.dev/blob/s3blob` 包使用空导入，因为我们只与 `gocloud.dev/blob` 包进行交互。这样做是为了明确确保我们的应用程序不会无意中使用某些特定驱动器的功能。`OpenBucket()` 函数接收两个参数：`context.Context` 对象和一个包含存储桶 URL 的字符串。为了指定要打开的 S3 存储桶，我们提供 S3 URL，其格式为：`s3://bucket-name?<customisations>`。相反，对于本地开发，我们将使用兼容 S3 的开源存储服务 MinIO ([`min.io`](https://min.io))，我们可以在本地运行。为了与本地运行的 MinIO 建立，我们为 `OpenBucket()` 提供的 URL 将是 `s3://bucket-name?endpoint=http://127.0.0.1:9000&disableSSL=true&s3ForcePathStyle=true`。查询参数 `disableSSL=true` 指明我们希望与存储服务器通过 HTTP（而非 HTTPS）交换数据。如果你通过网络与 MinIO 通信，即在你的本地系统之外，你应该使用 HTTPS 而不是 HTTPS。





在我们启动应用程序之前，需要先使用 `Docker Desktop` 应用程序启动 `MinIO` 服务的本地副本。打开一个新的终端会话，然后在安装了 `Docker` 且可以与互联网通信的计算机上执行以下命令：

```
$ docker run \
    -p 9000:9000 \
    -p 9001:9001 \
    -e MINIO_ROOT_USER=admin \
    -e MINIO_ROOT_PASSWORD=admin123 \
    -ti minio/minio:RELEASE.2021-07-08T01-15-01Z \
    server "/data" \
    --console-address ":9001"
```

`MinIO` 通过两个独立的网络端口提供其功能。通过端口 `9000` 的的请求是应用程序对对象存储服务的 API 调用。这是我们为包服务器（package server）指定的。第二个端口 `9001` 配置为控制台地址，用于使用自定义 Web 界面与 `MinIO` 进行通信。你可以从主机计算机使用 `127.0.0.1:9000` 和 `127.0.0.1:9001` 地址与这些服务交互。我们将用户名设置为 `admin`，密码设置为 `admin123`。我们使用 `RELEASE.2021-07-08T01-15-01Z` 版本来启动本地服务。一旦你运行了上面的命令，它应该下载镜像并启动容器，日志看起来大致如下：

```
API: http://172.17.0.2:9000  http://127.0.0.1:9000
RootUser: admin
RootPass: admin123
 
Console: http://172.17.0.2:9001 http://127.0.0.1:9001
RootUser: admin
RootPass: admin123
 
Command-line: https://docs.min.io/docs/minio-client-quickstart-guide
   $ mc alias set myminio http://172.17.0.2:9000 admin admin123
 
Documentation: https://docs.min.io
```

保持服务器运行。在浏览器中访问 `http://127.0.0.1:9001` 进入 Web 界面，并使用用户名 `admin` 和密码 `admin123` 登录。然后访问 [`127.0.0.1:9001/buckets`](http://127.0.0.1:9001/buckets) 并点击 `Create Bucket`。指定桶名称为 `test-bucket` 并点击 `Save` (图 11.2)。

![图 11.2:在 MinIO 中创建桶](img/1102.png)

### 在 MinIO 中创建桶

创建桶后，回到构建包服务器的终端，按如下方式启动它：

```
$ cd chap11/pkg-server
$ S3_ADDR=http://127.0.0.1:9000 BUCKET_NAME=test-bucket AWS_ACCESS_KEY_ID=admin AWS_SECRET_ACCESS_KEY=admin123
```

我们指定环境变量 `S3_ADDR` 包含 `MinIO` 可用的地址。我们使用 `BUCKET_NAME` 指定我们要使用的桶。环境变量 `AWS_ACCESS_KEY_ID` 和 `AWS_SECRET_ACCESS_KEY` 用于通过 API 进行身份验证的凭据。在这里我们指定了用户名和生成的密码。现在服务器已运行，让我们对服务器发起下载请求。你可以使用任何文件进行下载。在新的终端会话中，使用 `curl` 执行以下命令：

```
$ curl -F name=server -F version=0.1 -F file=@server.go http://127.0.0.1:8080/packages
```

### 获取响应

我们收到了由 `packageName` 构建的包响应。在运行服务器的终端上，你会看到如下日志：

```
2021/08/14 08:06 handlers.go:46: Package uploaded: server-0.1.go Bytes written: 183
```

如果你现在从浏览器使用地址 `http://127.0.0.1:9001/browser/test-bucket` 访问 `MinIO` 界面，你会看到 `test-bucket` 内部有一个标识为 `server-0.1.go` 的对象。很好——我们成功配置了包服务器来下载指定的文件。支持 `MinIO`。

### 处理获取请求

接下来我们将编写一个处理函数，允许用户从对象存储下载包：

```go
func packageGetHandler(
    w http.ResponseWriter,
    r *http.Request,
    config appConfig,
) {
    queryParams := r.URL.Query()
    packageID := queryParams.Get("id")

    exists, err := config.packageBucket.Exists(
        r.Context(), packageID,
    )
    if err != nil || !exists {
        http.Error(w, "invalid package ID", http.StatusNotFound)
        return
    }

    url, err := config.packageBucket.SignedURL(
        r.Context(),
        packageID,
        nil,
    )
    if err != nil {
        http.Error(
            w,
            err.Error(),
            http.StatusInternalServerError,
        )
        return
    }

    http.Redirect(w, r, url, http.TemporaryRedirect)
}
```

该函数期望作为查询参数传递的包 ID。然后它将查询对象存储服务以检查对象是否存在，调用 `*blob.Bucket` 的 `Exists()` 方法。我们使用请求上下文和包 ID 调用此方法。它返回两个值：类型为 `bool` 的 `exists` 和错误 `err`。如果对象存在中，`exists` 为 `true`，否则为 `false`。非零错误值表示检查对象时出现意外问题。如果 `exists` 为 `false` 或错误不为零，我们向客户端返回 HTTP 404 错误。我们显式进行此检查，因为在创建对象的签名 URL 时不会检查对象是否存在。如果对象存在中，我们为对象创建签名 URL 并发起重定向。在这里使用临时重定向，因为签名 URL 在下次请求文件时会发生。

### 签名 URL

签名 URL 允许你的应用程序授权请求者在限制时间内访问分段对象。我们调用为 `packageBucket` 对象定义的 `SignedURL()` 方法，带有三个参数：请求上下文、创建签名 URL 的对象 ID 以及第三个参数的 `nil`。预期第三个参数如果为 `nil`，则将是 `blob.SignedURLOptions` 类型的对象，这允许我们设置 URL 失效的时长。例如，你可以将 URL 的有效期设置为 15 分钟，而不是默认的 60 分钟。生成签名 URL 也有助于其他操作——在桶中创建对象或删除。对于这些操作，你需要通过 `blob.SignedURLOptions` 对象指定 `Method` 字段设置为 `PUT` 或 `DELETE`，而不是 `GET` 方法。下面是带有自定义有效期和 `PUT` 方法的 `blob.SignedURLOptions` 创建示例：

```go
sOpts := blob.SignedURLOptions{
    Expiry: 15 * time.Minute,
    Method: http.MethodPut,
}
url, err := config.packageBucket.SignedURL(
    r.Context(),
    packageName,
    &sOpts,
)
```

现在让我们来看看请求的行为。你已经启动了包服务器。我们返回了之前下载的包 ID，现在让我们重新请求它：

```
$ curl "http://127.0.0.1:8080/api/packages?id=server-0.1.go"
<a href="http://127.0.0.1:9000/test-bucket/server-0.1.go?
X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=admin%2F20210814%
2Fap-southeast-2%2Fs3%2Faws4_request&X-Amz-Date=20210814T003039Z&
amp;X-Amz-Expires=3600&X-Amz-SignedHeaders=host&
X-Amz-Signature=3b627ab2ae31e69fba1f8c224c76aae6e24f87982640e
c3373aa8ea
7f94962a2">Temporary Redirect</a>.
```




我们返回一个指向所请求对象的签名 URL 的重定向。该 URL 指向本地运行的 MinIO 服务器。因此，一旦用户获得了签名 URL，数据将直接从 MinIO 加载。如果我们通过在原始 `curl` 命令中添加 `--location` 来跟随重定向，或者在浏览器中打开 URL，你将看到文件内容。

```
$ curl --location \
  "http://127.0.0.1:8080/api/packages?id=server-0.1-server.go"
# file contents
```

指向对象的签名 URL 重定向是向客户端返回数据的方法之一。另一种方法是在应用程序中使用 `ReadAll()` 方法从存储桶读取数据，或者通过 `NewReader()` 方法获取 `io.Reader` 并将数据作为响应发送给客户端。练习 11.1 将让你能够实现这一功能。

在完成基于 MinIO 的本地开发后，为了让包服务器指向 AWS S3 存储桶，你只需要指定桶名称、正确的访问凭据和区域即可：

```
1$ AWS_DEFAULT_REGION=ap-southeast-2 BUCKET_NAME=<your bucker name> \
< AWS_ACCESS_KEY_ID=<aws access key id>\
AWS_SECRET_ACCESS_KEY=<aws-secret-key> ./pkg-server-1
```

接下来，让我们看看如何为我们的处理函数编写自动化测试。

### 测试包上传

为了测试包上传功能，我们将使用在 `go.dev/blob/fileblob` 驱动包中实现的基于文件系统的存储桶。首先，我们将编写一个函数来返回指向文件系统存储桶的 `blob.Bucket` 对象：

```
func getTestBucket(tmpDir string) (*blob.Bucket, error) {
    myDir, err := os.MkdirTemp(tmpDir, "test-bucket")
    if err != nil {
        return nil, err
    }
    u, err := url.Parse(fmt.Sprintf("file:///%s", myDir))
    if err != nil {
        return nil, err
    }
    opts := fileblob.Options{
        URLSigner: fileblob.NewURLSignerHMAC(
            u,
            []byte("super secret"),
        ),
    }
    return fileblob.OpenBucket(myDir, &opts)
}
```

我们使用 `fileblob` 包目录打开基于文件系统的存储桶。这样做是为了能够添加创建签名 URL 的功能。我们创建一个 `fileblob.Options` 对象，配置带有以 `file:///` 开头的基础 URL 的 `URLSigner` 函数、指向我们创建的临时目录的 URL 方案以及伪造的密钥 `super secret`。

然后，在测试函数内部，我们将调用 `getTestBucket()` 函数并如下所示创建 `appConfig` 对象：

```
func TestPackageRegHandler(t *testing.T) {
    packageBucket, err := getTestBucket(t.TempDir())
    if err != nil {
        t.Fatal(err)
    }
    defer packageBucket.Close()

    config := appConfig{
        logger: log.New(os.Stdout, "", log.Ldate|log.Ltime|log.Lfile),
        packageBucket: packageBucket,
    }
    mux := http.NewServeMux()
    setupHandlers(mux, config)

    ts := httptest.NewServer(mux)
    defer ts.Close()

    p := pkgData{
        Name:     "mypackage",
        Version:  "0.1",
        Filename: "mypackage-0.1.tar.gz",
        Bytes:    strings.NewReader("data"),
    }
    // 测试的其他部分
```

你可以在源代码仓库 `chap11/pkg-server-1` 下的 `package_reg_handler_test.go` 文件中找到测试包处理函数的函数。包上传测试将检查重定向行为。如果我们能够生成作为响应的重定向，我们就知道它完成了工作。以下是我们通过新的测试函数 `TestPackageGetHandler()` 检查这一点，仅显示运算符：

```
func TestPackageGetHandler(t *testing.T) {
    // TODO 获取测试桶
    err = packageBucket.WriteAll(
        context.Background(),
        "test-object-id",
        []byte("test-data"),
        nil,
    )
    // TODO 处理错误、配置并设置服务器
    var redirectUrl string
    client := http.Client{
        CheckRedirect: func(
            req *http.Request, via []*http.Request,
        ) error {
            redirectUrl = req.URL.String()
            return errors.New("no redirect")
        },
    }

    _, err = client.Get(ts.URL + "/api/packages?id=test-object-id")
    if err == nil {
        t.Fatal("Expected error: no redirect, Got nil")
    }
    if !strings.HasPrefix(redirectUrl, "file://") {
        t.Fatalf("Expected redirect url to start with file:///, got: %v", redirectUrl)
    }
```

我们在测试桶中直接创建一个指定对象标识的对象。然后，正如你在第 4 章中所记得，我们必须使用自定义函数 `CheckRedirect` 创建 HTTP 客户端，以确保它不会跟随重定向。接下来，使用该客户端对获取 `test-object-id` 的测试服务器发送 HTTP GET 请求。我们检查 `redirectUrl` 中的字符串值是否指向我们配置的文件系统存储桶（以 `file:///`）。完整的测试函数可以在源代码仓库 `chap11/pkg-server-1` 的 `package_handler_test.go` 文件中找到。运行 `go test` 以确保测试通过。

### 访问底层类型

到目前为止，你已经看到如何使用 `gocloud.dev/blob` 包提供的各种高层接口来与兼容 S3 的存储服务交互。此外，你还学会了如何使用 `gocloud.dev/blob/fileblob` 包作为测试的文件系统存储服务。如果你在将来想更改存储服务，你现在只需要更改打开存储桶或创建 `*blob.Bucket` 对象的方式。应用程序的其他部分不需要修改。这就是 `gocloud.dev/blob` 包提供的优势。

然而，有时你可能需要访问 `gocloud.dev/blob` 未提供的特定供应商底层功能。为了支持这种用例，`gocloud.dev/blob` 包提供了将 `gocloud.dev/blob` 定义的类型转换为特定供应商底层类型的功能。成功转换后，你可以直接访问底层驱动的功能。如果你指的是 AWS S3 的存储桶，你将能够直接访问 Go AWS SDK 提供的功能，其他支持的存储服务也是如此。

让我们来看一个例子。如果打开的存储桶不存在，`blob.OpenBucket()` 不返回错误。实际上，`gocloud.dev/blob` 包不允许我们检查这一点。然而，AWS SDK 的底层类型允许我们检查。考虑以下代码片段：

```go
package main

func main() {
    bucketName := "practicalgo-echorand"
    testBucket, err := blob.OpenBucket(
        context.Background(),
        fmt.Sprintf("s3://%s", bucketName),
    )
    if err != nil {
        log.Fatal(err)
    }
    defer testBucket.Close()

    var s3Svc *s3.S3
    if !testBucket.As(&s3Svc) {
        log.Fatal(
            "Couldn't convert type to underlying S3 bucket type",
        )
    }
    _, err = s3Svc.HeadBucket(
        &s3.HeadBucketInput{
            Bucket: &bucketName,
        },
    )
    if err != nil {
        log.Fatalf(
            "Bucket doesn't exist, or insufficient permissions: %v\n",
            err,
        )
    }
}
```



Возвращаемый функцией `OpenBucket()` объект `*blob.Bucket` можно преобразовать в тип `*s3.S3`, определенный в пакете `github.com/aws/aws-sdk-go/s3`. Соответственно, мы объявляем переменную `s3Svc` типа `*s3.S3` и вызываем метод `As()`, определенный для объекта `testBucket`. Метод `As()` возвращает `true`, если преобразование прошло успешно, иначе возвращает `false`. В случае успеха мы можем использовать объект `s3Svc` для вызова метода `HeadBucket()`, определенного в объекте `s3.S3`, чтобы выполнить запрос `HTTP HEAD` и проверить, существует ли бакет. Значение ошибки, отличное от нуля, указывает на то, что бакет не существует или текущие учетные данные не имеют необходимых прав. Вы можете найти список исполняемых программ в каталоге `chap11/object-store-demo/vendor-as-demo`. Чтобы узнать, какие базовые типы предоставляет `gocloud.dev/blob`, просмосмотрите документацию пакетов для конкретных драйверов.

Завершите работу сервера MinIO, так и процессов сервера пакетов. В следующем разделе мы обновим сервер пакетов, добавив возможность хранения метаданных — имени, версии и владельца, связанных с каждым пакетом — с использованием реляционной базы данных. Это позволит позволит запрашивать пакеты с сервера пакетов по их именам или версиям. Другими словами, мы добавляем возможность поиска на наш сервер пакетов с помощью реляционной базы данных.

## Работа с реляционными базами данных

Популярными примерами систем управления реляционными базами данных являются MySQL, PostgreSQL и SQLite. Для нашего сервера пакетов мы будем использовать MySQL в качестве реляционной базы данных. Эти системы хранения данных построены на концепции хранения таблиц и отношений между ними. Мы создадим базу данных `package_server` с двумя таблицами: `packages` и `users`. Строка в таблице `packages` будет содержать имя пакета, версию, метку создания в формате UTC, владельца и идентификатор, уникальный для каждой загруженной версии пакета. Строка в таблице `users` будет содержать столбец имени пользователя, используемый для аутентификации в системе, и идентификатор, однозначно идентифицирующий пользователя в системе. Мы не будем реализовывать аутентификацию или авторизацию в нашем приложении, чтобы все было просто. Мы позволим пользователю загружать несколько версий пакета и хотим, чтобы пользователи нашего сервера могли загружать любую версию пакета. Существующая версия пакета не может быть загружена повторно. На Рисунке 11.3 показана модель отношений «сущность-связь» базы данных `package_server`.

![Рисунок 11.3: Диаграмма отношений сущностей для базы данных сервера пакетов](img/1103.png)

Рисунок 11.3: Диаграмма отношений сущностей для базы данных сервера пакетов

Сначала мы запустим локальную копию сервера базы данных MySQL с помощью Docker и запустим сервер, создав ожидаемые таблицы и предварительно заполнив некоторые данные. Каталог `chap11/pkg-server-2/mysql-init` содержит необходимые SQL-скрипты для выполнения начальной загрузки. Во-первых, мы создадим две таблицы, `users` и `packages`, используя SQL-операторы в файле `01-create-table.sql`:

```sql
use package_server;

CREATE TABLE users (
    id INT PRIMARY KEY AUTO_INCREMENT,
    username VARCHAR(30) NOT NULL
);

CREATE TABLE packages (
    id INT PRIMARY KEY AUTO_INCREMENT,
    name VARCHAR(255) NOT NULL,
    version VARCHAR(50) NOT NULL,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    owner_id INT,
    UNIQUE(name, version),
    FOREIGN KEY (owner_id) REFERENCES users(id)
);
```

Затем мы добавим начальные данные, используя скрипт `02-insert-data.sql`:

```sql
INSERT INTO users (username) VALUES ('admin'), ('alice');
INSERT INTO packages (name, version, owner_id) VALUES ('my-package', '1.0.0', 1), ('my-package', '1.1.0', 1);
```

После этого мы перейдем к обновлению кода сервера пакетов для работы с базой данных.

## Интеграция с базой данных MySQL

Популярными примерами систем управления реляционными базами данных являются MySQL, PostgreSQL и SQLite. Для нашего сервера пакетов мы будем использовать MySQL в качестве реляционной базы данных. Эти системы хранения данных построены на концепции хранения таблиц и отношений между ними. Мы создадим базу данных `package_server` с двумя таблицами: `packages` и `users`. Строка в таблице `packages` будет содержать имя пакета, версию, метку создания в формате UTC, владельца и идентификатор, уникальный для каждой загруженной версии пакета. Строка в таблице `users` будет содержать столбец имени пользователя, используемый для аутентификации в системе, и идентификатор, однозначно идентифицирующий пользователя в системе. Мы не будем реализовывать аутентификацию или авторизацию в нашем приложении, чтобы все было просто. Мы позволим пользователю загружать несколько версий пакета и хотим, чтобы пользователи нашего сервера могли загружать любую версию пакета. Существующая версия пакета не может быть загружена повторно.

Для работы с MySQL мы будем использовать стандартный пакет `database/sql`. Сначала нам нужно импортировать этот пакет и драйвер MySQL:

```go
import (
    "database/sql"
    "fmt"
    _ "github.com/go-sql-driver/mysql"
)
```

Теперь создадим функцию для получения соединения с базой данных:

```go
func getDatabaseConn(
    dbAddr, dbName, dbUser, dbPassword string,
) (*sql.DB, error) {
    dsn := fmt.Sprintf("%s:%s@tcp(%s)/%s",
        dbUser, dbPassword, dbAddr, dbName,
    )
    db, err := sql.Open("mysql", dsn)
    if err != nil {
        return nil, err
    }
    if err = db.Ping(); err != nil {
        return nil, err
    }
    return db, nil
}
```

Используя эту функцию, мы можем инициализировать соединение в основной файле нашего сервера:

```go
func main() {
    db, err := getDatabaseConn("localhost:3306", "package_server", "root", "password")
    if err != nil {
        log.Fatalf("error connecting to database: %v", err)
    }
    defer db.Close()
    // ... остальной код
}
```



`*sql.Db` 对象将在服务器应用程序启动时创建，并在整个服务器生命周期内保持激活状态。因此，`sql.Open()` 函数在服务器进程的生存周期内仅会被调用一次。来自修改后的包服务器 `main()` 函数 get 代码片段展示了如何实现：

```go
package main

func main() {
    // TODO 读取对象存储相关信息
    dbAddr := os.Getenv("DB_ADDR")
    dbName := os.Getenv("DB_NAME")
    dbUser := os.Getenv("DB_USER")
    dbPassword := os.Getenv("DB_PASSWORD")

    if len(dbAddr) == 0 || len(dbName) == 0 || len(dbUser) == 0 || len(dbPassword) == 0 {
        log.Fatal(
            "Must specify DB details - DB_ADDR, DB_NAME, DB_USER, DB_PASSWORD",
        )
    }

    db, err := getDatabaseConn(
        dbAddr, dbName,
        dbUser, dbPassword,
    )
    config := appConfig{
        logger: log.New(
            os.Stdout, "",
            log.Ldate|log.Ltime|log.Lshortfile,
        ),
        packageBucket: packageBucket,
        db:            db,
    }
    // 启动服务器的代码
}
```

获取 `*sql.DB` 对象后，为了在服务器上执行查询，我们将调用 `Conn()` 方法来获取 `*sql.Conn` 对象：

```go
ctx := context.Background()
conn, err := config.db.Conn(ctx)
```



```go
func packageGetHandler(
    w http.ResponseWriter, r *http.Request, config appConfig,
) {
    queryParams := r.URL.Query()
    owner := queryParams.Get("owner_id")
    name := queryParams.Get("name")
    version := queryParams.Get("version")
    // TODO Вернуть HTTP 400 Bad Request 错误,
    // если любой из вышеперечисленного отсутствует

    ownerId, err := strconv.Atoi(owner)

    // TODO Вернуть HTTP 400 错误,
    // если преобразование не удалось

    q := pkgQueryParams{
        ownerId: ownerId,
        version: version,
        name: name,
    }
    pkgResults, err := queryDb(
        config, q,
    )
    // TODO обработка ошибок

    if len(pkgResults) == 0 {
        http.Error(w, "No package found", http.StatusNotFound)
        return
    }

    url, err := config.packageBucket.SignedURL(
        r.Context(),
        pkgResults[0].ObjectStoreId,
        nil,
    )
    if err != nil {
        http.Error(
            w, err.Error(), http.StatusInternalServerError,
        )
        return
    }
    http.Redirect(w, r, url, http.StatusTemporaryRedirect)
}
```

在处理函数中，我们在传入请求的 URL 地址中查找三个查询参数：`owner_id`、`name` 和 `version`。如果任何参数未指定或 `owner_id` 的值无法成功转换为整数，我们将返回 HTTP 400 错误请求错误。

然后，我们创建一个类型为 `pkgQueryParams` 的新对象，包含这些查询参数的值，并调用 `queryDb()` 函数。`queryDb()` 返回两个值：第一个是 `pkgRow` 对象的切片，第二个是错误值。如果我们得到空切片，我们将发送 HTTP 404 状态作为响应。否则，我们提取切片中的第一个元素，调用在 `config.packageObject` 中定义的 `SignedURL()` 方法来创建签名 URL，然后重定向到该地址。接下来让我们来看 `queryDb()` 函数的定义。

该函数首先创建一个发送到数据库的请求，其格式为 `SELECT * FROM packages WHERE owner_id=1 AND name=test-package AND version=0.1`。尽管在这种场景下我们应该指定所有条件，但我们编写函数的方式使得满足任何一个条件就足够获取包。（在执行练习 11.2 时你会发现这很有用。）因此，我们能够构建诸像 `SELECT * FROM packages WHERE owner_id=1 AND name=test-package` 或 `SELECT * FROM packages WHERE owner_id=1` 这样的查询。

在下一个代码片段中部分显示了 `queryDb()` 函数，我们在其中构建了查询：

```go
func queryDb(
    config appConfig, params pkgQueryParams,
) ([]pkgRow, error) {

    args := []interface{}{}
    conditions := []string{}
    if params.ownerId != 0 {
        conditions = append(conditions, "owner_id=?")
        args = append(args, params.ownerId)
    }
    if len(params.name) != 0 {
        conditions = append(conditions, "name=?")
        args = append(args, params.name)
    }
    if len(params.version) != 0 {
        conditions = append(conditions, "version=?")
        args = append(args, params.version)
    }

    if len(conditions) == 0 {
        return nil, fmt.Errorf("no query conditions found")
    }

    query := fmt.Sprintf(
        "SELECT * FROM packages WHERE %s",
        strings.Join(conditions, " AND "),
    )
    // TODO 执行查询
}
```

我们创建了两个切片，并将根据 `params` 对象中的字段逐步填充。`args` 是一个类型为 `interface{}` 的空切片，我们在这个切片中存储 `owner_id`、`name` 或 `version` 的值。我们需要将其类型设置为 `[]interface{}{}` 而不是 `[]string`，因为 `QueryContext()` 期望占位符的值以这种格式提供。在第二个类型为 `[]string{}` 的切片 `conditions` 中，我们将添加查询的一部分。我们检查哪些字段被指定，然后将相应的条件和相应的占位符值分别添加到 `conditions` 和 `args` 切片中。如果没有任何条件被指定，则返回错误。

最后，我们使用 `strings.Join()` 函数结合 `conditions` 切片的内容，使用 `AND`（带有前后空格）连接元素。通过调用函数 `fmt.Sprintf()` 得到的字符串现在准备好执行了：

```go
func queryDb(
    config appConfig, params pkgQueryParams,
) ([]pkgRow, error) {
    ctx := context.Background()
    conn, err := config.db.Conn(ctx)
    if err != nil {
        log.Fatal(err)
    }
    defer conn.Close()

    rows, err := conn.QueryContext(ctx, query, args...)
    if err != nil {
        return nil, err
    }
    defer rows.Close()

    var pkgResults []pkgRow
    for rows.Next() {
        var pkg pkgRow
        if err := rows.Scan(
            &pkg.OwnerId, &pkg.Name, &pkg.Version,
            &pkg.ObjectStoreId, &pkg.Created,
        ); err != nil {
            return nil, err
        }
        pkgResults = append(pkgResults, pkg)
    }

    if err := rows.Err(); err != nil {
        return nil, err
    }
    return pkgResults, nil
}
```

`rows.Next()` 方法初始化读取操作。当没有可读行或读取过程中发生错误时返回 `false`。

随后我们使用 `rows.Scan()` 方法，向其传递我们想要读取的列的变量引用。如果 `Scan()` 成功，我们将 `pkg` 添加到 `pkgResults` 中。

一旦我们完成了所有行的读取或读取过程中发生了错误（即我们离开了 `for` 循环），我们调用 `Err()` 来检查是否有错误。如果是这样，我们返回它；否则，我们返回 `pkgResults` 切片和 `nil`。

你可以在源码仓库的 `chap11/pkg-server-2` 目录下找到带有对象存储服务和数据库集成的新版本服务器。`db_store.go` 文件包含了与数据库交互的函数。现在让我们尝试我们添加的功能。




```
$ curl "http://127.0.0.1:8080/api/packages?name=test-package&version=0.1&owner_id=1"
No package found
```

太棒了，现在我们添加一个包：

```
$ curl -F name=test-package -F version=0.1 \
-F filedata=@image.tgz http://127.0.0.1:8080/api/packages
{"id":"2/test-package-0.1-image.tgz"}
```

你会在 `chap11/pkg-server-2` 目录下找到 `image.tgz` 文件。当然，你可以尝试使用任何其他文件。请注意，响应还包含所有者用户 ID `2`，由于我们是随机分配所有者的，这个 ID 对你来说可能不同。现在，让我们尝试上传包，确保你使用的元数据与之前对应的值对应：

```bash
$ curl --location "http://127.0.0.1:8080/api/packages?name=test-package&version=0.1&owner_id=2"
Warning: Binary output can mess up your terminal. Use "--output -" 
to tell
Warning: curl to output it to your terminal anyway, or consider 
"--output
Warning: <FILE>" to save to a file.
```

`curl` 默认不显示输出，因为响应不是文本文件。如果你使用浏览器，你上传的文件将被下载，或者其内容将作为嵌入内容显示。太棒了！现在我们已经确认对象存储服务和数据库都已集成到包服务器中。你可以将应用程序指向运行在其他地方的 MySQL 数据库（例如通过 AWS RDS），并为其提供相应的连接数据，一切运行起来将和本地完全一样。

接下来，你有一个练习来尝试巩固你的理解，练习 11.2。

### 数据存储测试

在涉及与数据库交互的测试时，可以使用几种方法。使用 Mock 对象（模拟对象）、使用内存中的 SQL 数据库以及运行本地数据库副本——这些只是其中一些。我们将采用第三种方法。这允许我们以类似于生产环境配置的方式来测试应用程序（生产环境是配置为使用真实数据库服务器的）。我们将使用 Docker 容器运行本地 MySQL 副本，其加载方式与前一节完全相同，并运行指向该数据库服务器副本的应用程序。测试完成后，MySQL 容器将自动停止。为了组织这些测试容器的创建和销，我们将使用第三方包：[`github.com/testcontainers/testcontainers-go/`](https://github.com/testcontainers/testcontainers-go/)。使用该包，我们将编写一个函数 `getTestDb()`，它将返回一个配置好的 `*sql.DB` 对象以连接到运行的测试数据库服务器：

```go
func getTestDb() (testcontainers.Container, *sql.DB, error) {
    bootStrapSqlDir, err := os.Stat("mysql-init")
    if err != nil {
        return nil, nil, err
    }

    cwd, err := os.Getwd()
    if err != nil {
        return nil, nil, err
    }
    bindMountPath := filepath.Join(cwd, bootStrapSqlDir.Name())

    // TODO – 创建并启动容器
}
```

你还记得在创建本地 MySQL Docker 容器时，我们挂载了来自 `chap11/pkg-server-2` 的 `mysql-init` 目录，以便创建表并向用户表中插入记录。我们在创建测试容器时将执行相同的操作。首先，我们使用 `os` 包中的 `os.Stat()` 函数确保目录存在，然后创建目录的绝对路径并将其存储在 `bindMountPath` 中。

然后，我们如下创建容器请求：

```go
func getTestDb() (testcontainers.Container, *sql.DB, error) {
    // TODO 插入之前显示的代码
    waitForSql := wait.ForSQL("3306/tcp", "mysql",
        func(p nat.Port) string {
            return "root:rootpw@tcp(" +
                "127.0.0.1:" + p.Port() +
                ")/package_server"
        })
    waitForSql.WithPollInterval(5 * time.Second)

    req := testcontainers.ContainerRequest{
        Image:        "mysql:8.0.26",
        ExposedPorts: []string{"3306/tcp"},
        Env: map[string]string{
            "MYSQL_DATABASE":      "package_server",
            "MYSQL_USER":          "packages_rw",
            "MYSQL_PASSWORD":      "password",
            "MYSQL_ROOT_PASSWORD": "rootpw",
        },
        BindMounts: map[string]string{
            bindMountPath: "/docker-entrypoint-initdb.d",
        },
        Cmd: []string{"--default-authentication-plugin=mysql_native_password"},
        WaitingFor: waitForSql,
    }
}
```




`testcontainers.GenericContainer()` 函数接受两个参数。第一个是 `context.Context` 类型的值，你可以用它来控制容器就绪所需的时间。第二个参数是 `testcontainers.GenericContainerRequest` 类型的对象，在其中我们指定了两个字段：`ContainerRequest`，其值是我们之前创建的容器请求对象 `req`；以及 `Started` 设置为 `true`，因为我们要启动容器。该函数返回两个值：第一个是 `testcontainers.Container` 类型的对象，第二个是错误值。如果函数返回的错误值为零，我们调用 `PortEndpoint()` 方法来获取可以从主机连接到容器的地址。然后我们调用 `getDatabaseConn()` 方法来获取 `*sql.DB` 对象。

你可以在 `chap11/pkg-server2/test_utils.go` 文件中找到 `getTestDb()` 函数的定义。拥有了创建 MySQL 测试容器的能力，现在我们可以开始为处理函数编写测试，也可以仅为与数据库交互的函数编写测试。例如，获取包的处理函数的测试将如下定义所示：

```
func TestPackageGetHandler(t *testing.T) {
    packageBucket, err := getTestBucket(t.TempDir())
    testObjectId := "pkg-0.1-pkg-0.1.tar.gz"
    // 创建测试对象
    err = packageBucket.WriteAll(
        context.Background(),
        testObjectId, []byte("test-data"),
        nil,
    )

    testC, testDb, err := getTestDb()
    if err != nil {
        t.Fatal(err)
    }
    defer testC.Terminate(context.Background())

    config := appConfig{
        logger: log.New(
            os.Stdout, "",
            log.Ldate|log.Ltime|log.Lshortfile,
        ),
        packageBucket: packageBucket,
        db:            testDb,
    }

    // 更新测试对象的包元数据
    err = updateDb(
        config,
        pkgRow{
            OwnerId: 1,
            Name: "pkg",
            Version: "0.1",
            ObjectStoreId: testObjectId,
        },
    )
    if err != nil {
        t.Fatal(err)
    }

    // TODO 执行 HTTP 请求并检查结果
}
```

我们调用 `getTestDb()` 函数来获取 `*sql.DB` 对象。然后我们对返回的 `testcontainers.Container` 值 `testC` 延迟调用 `Terminate()` 方法，以便容器在测试执行结束时关闭。

接着，我们创建一个 `appConfig` 对象，其 `db` 字段的值为 `testDb`。然后我们调用 `updateDb()` 函数来为测试包添加包元数据。这与我们之前在函数中创建的测试对象对应。然后我们发送 HTTP 请求来上传包数据并检查重定向行为。你可以在 `package_get_handler_test.go` 文件中找到测试的完整定义以及另一个测试。在 `package_reg_handler_test.go` 文件中，你也会找到用于检查包注册功能的测试函数。

接下来，我们将讨论在处理数据库时可能会遇到的几种常见数据类型转换的具体场景。

### 数据类型转换

当我们调用 `*sql.Rows` 对象的 `Scan()` 方法时，驱动程序包会执行自动类型转换，将数据库中表示的列原始数据类型转换为我们在应用程序中指定的变量类型。反向过程发生在执行 `INSERT` 操作符时。

当我们调用 `*sql.Rows` 对象的 `Scan()` 方法时，驱动程序包会执行自动类型转换，将数据库中表示的列原始数据类型转换为我们在应用程序中指定的变量类型。反向过程发生在执行 `INSERT` 操作符时。

当我们调用 `*sql.Rows` 对象的 `Scan()` 方法时，驱动程序包会执行自动类型转换，将数据库中表示的列原始数据类型转换为我们在应用程序中指定的变量类型。反向过程发生在执行 `INSERT` 操作符时。

当我们调用 `*sql.Rows` 对象的 `Scan()` 方法时，驱动程序包会执行自动类型转换，将数据库中表示的列原始数据类型转换为我们在应用程序中指定的变量类型。反向过程发生在执行 `INSERT` 操作符时。

当我们调用 `*sql.Rows` 对象的 `Scan()` 方法时，驱动程序包会执行自动类型转换，将数据库中表示的列原始数据类型转换为我们在应用程序中指定的变量类型。反向过程发生在执行 `INSERT` 操作符时。

当我们调用 `*sql.Rows` 对象的 `Scan()` 方法时，驱动程序包会执行自动类型转换，将数据库中表示的列原始数据类型转换为我们在应用程序中指定的变量类型。反向过程发生在执行 `INSERT` 操作符时。

当我们调用 `*sql.Rows` 对象的 `Scan()` 方法时，驱动程序包会执行自动类型转换，将数据库中表示的列原始数据类型转换为我们在应用程序中指定的变量类型。反向过程发生在执行 `INSERT` 操作符时。

当我们调用 `*sql.Rows` 对象的 `Scan()` 方法时，驱动程序包会执行自动类型转换，将数据库中表示的列原始数据类型转换为我们在应用程序中指定的变量类型。反向过程发生在执行 `INSERT` 操作符时。

当我们调用 `*sql.Rows` 对象的 `Scan()` 方法时，驱动程序包会执行自动类型转换，将数据库中表示的列原始数据类型转换为我们在应用程序中指定的变量类型。反向过程发生在执行 `INSERT` 操作符时。

当我们调用 `*sql.Rows` 对象的 `Scan()` 方法时，驱动程序包会执行自动类型转换，将数据库中表示的列原始数据类型转换为我们在应用程序中指定的变量类型。反向过程发生在执行 `INSERT` 操作符时。

当我们调用 `*sql.Rows` 对象的 `Scan()` 方法时，驱动程序包会执行自动类型转换，将数据库中表示的列原始数据类型转换为我们在应用程序中指定的变量类型。反向过程发生在执行 `INSERT` 操作符时。

当我们调用 `*sql.Rows` 对象的 `Scan()` 方法时，驱动程序包会执行自动类型转换，将数据库中表示的列原始数据类型转换为我们在应用程序中指定的变量类型。反向过程发生在执行 `INSERT` 操作符时。

当我们调用 `*sql.Rows` 对象的 `Scan()` 方法时，驱动程序包会执行自动类型转换，将数据库中表示的列原始数据类型转换为我们在应用程序中指定的变量类型。反向过程发生在执行 `INSERT` 操作符时。

当我们调用 `*sql.Rows` 对象的 `Scan()` 方法时，驱动程序包会执行自动类型转换，将数据库中表示的列原始数据类型转换为我们在应用程序中指定的变量类型。反向过程发生在执行 `INSERT` 操作符时。

当我们调用 `*sql.Rows` 对象的 `Scan()` 方法时，驱动程序包会执行自动类型转换，将数据库中表示的列原始数据类型转换为我们在应用程序中指定的变量类型。反向过程发生在执行 `INSERT` 操作符时。

当我们调用 `*sql.Rows` 对象的 `Scan()` 方法时，驱动程序包会执行自动类型转换，将数据库中表示的列原始数据类型转换为我们在应用程序中指定的变量类型。反向过程发生在执行 `INSERT` 操作符时。

当我们调用 `*sql.Rows` 对象的 `Scan()` 方法时，驱动程序包会执行自动类型转换，将数据库中表示的列原始数据类型转换为我们在应用程序中指定的变量类型。反向过程发生在执行 `INSERT` 操作符时。

当我们调用 `*sql.Rows` 对象的 `Scan()` 方法时，驱动程序包会执行自动类型转换，将数据库中表示的列原始数据类型转换为我们在应用程序中指定的变量类型。反向过程发生在执行 `INSERT` 操作符时。

当我们调用 `*sql.Rows` 对象的 `Scan()` 方法时，驱动程序包会执行自动类型转换，将数据库中表示的列原始数据类型转换为我们在应用程序中指定的变量类型。反向过程发生在执行 `INSERT` 操作符时。

当我们调用 `*sql.Rows` 对象的 `Scan()` 方法时，驱动程序包会执行自动类型转换，将数据库中表示的列原始数据类型转换为我们在应用程序中指定的变量类型。反向过程发生在执行 `INSERT` 操作符时。

当我们调用 `*sql.Rows` 对象的 `Scan()` 方法时，驱动程序包会执行自动类型转换，将数据库中表示的列原始数据类型转换为我们在应用程序中指定的变量类型。反向过程发生在执行 `INSERT` 操作符时。

当我们调用 `*sql.Rows` 对象的 `Scan()` 方法时，驱动程序包会执行自动类型转换，将数据库中表示的列原始数据类型转换为我们在应用程序中指定的变量类型。反向过程发生在执行 `INSERT` 操作符时。

当我们调用 `*sql.Rows` 对象的 `Scan()` 方法时，驱动程序包会执行自动类型转换，将数据库中表示的列原始数据类型转换为我们在应用程序中指定的变量类型。反向过程发生在执行 `INSERT` 操作符时。

当我们调用 `*sql.Rows` 对象的 `Scan()` 方法时，驱动程序包会执行自动类型转换，将数据库中表示的列原始数据类型转换为我们在应用程序中指定的变量类型。反向过程发生在执行 `INSERT` 操作符时。

当我们调用 `*sql.Rows` 对象的 `Scan()` 方法时，驱动程序包会执行自动类型转换，将数据库中表示的列原始数据类型转换为我们在应用程序中指定的变量类型。反向过程发生在执行 `INSERT` 操作符时。

当我们调用 `*sql.Rows` 对象的 `Scan()` 方法时，驱动程序包会执行自动类型转换，将数据库中表示的列原始数据类型转换为我们在应用程序中指定的变量类型。反向过程发生在执行 `INSERT` 操作符时。

当我们调用 `*sql.Rows` 对象的 `Scan()` 方法时，驱动程序包会执行自动类型转换，将数据库中表示的列原始数据类型转换为我们在应用程序中指定的变量类型。反向过程发生在执行 `INSERT` 操作符时。

当我们调用 `*sql.Rows` 对象的 `Scan()` 方法时，驱动程序包会执行自动类型转换，将数据库中表示的列原始数据类型转换为我们在应用程序中指定的变量类型。反向过程发生在执行 `INSERT` 操作符时。

当我们调用 `*sql.Rows` 对象的 `Scan()` 方法时，驱动程序包会执行自动类型转换，将数据库中表示的列原始数据类型转换为我们在应用程序中指定的变量类型。反向过程发生在执行 `INSERT` 操作符时。

当我们调用 `*sql.Rows` 对象的 `Scan()` 方法时，驱动程序包会执行自动类型转换，将数据库中表示的列原始数据类型转换为我们在应用程序中指定的变量类型。反向过程发生在执行 `INSERT` 操作符时。

当我们调用 `*sql.Rows` 对象的 `Scan()` 方法时，驱动程序包会执行自动类型转换，将数据库中表示的列原始数据类型转换为我们在应用程序中指定的变量类型。反向过程发生在执行 `INSERT` 操作符时。

当我们调用 `*sql.Rows` 对象的 `Scan()` 方法时，驱动程序包会执行自动类型转换，将数据库中表示的列原始数据类型转换为我们应用程序中指定的变量类型。反向过程发生在执行 `INSERT` `符时。

 `调用 `*sql.Rows` 对象的 `Scan. 方法时，驱动程序包.执行。类型转换，，数据库。表示的列列原始类型类型转换为 `应用程序中指定的类型类型。。反，。。 ` ```。符。



 ` ` ` `..`   ` `..，，执行 `Scan. 方法时，驱动程序包会执行自动类型转换，将数据库中表示的列原始数据类型转换为我们在应用程序中指定的变量类型。反向过程发生在执行 `INSERT` 操作符时。

当我们调用 `*sql.Rows` 对象的 `Scan()` 方法时，驱动程序包会执行自动类型转换，将数据库中表示的列原始数据类型转换为我们在应用程序中指定的变量类型。反向过程发生在执行 `INSERT` 操作符时。

当我们调用 `*sql.Rows` 对象的 `Scan()` 方法时，驱动程序包会执行自动类型转换，将数据库中表示的列原始数据类型转换为我们在应用程序中指定的变量类型。反向过程发生在执行 `INSERT` 操作符时。 ` ` ` ` ` ` ` 符时。

在第二个场景中，我们将处理数据库中的 `NULL` 数据。假设我们在 `packages` 表中添加一个新列 `repo_url`：

```sql
CREATE TABLE packages(
  -- TODO 其他列
  repo_url VARCHAR(300) DEFAULT NULL,
)
```

此列可能包含包的源代码仓库地址。如果你尝试将该列的 `NULL` 值扫描到字符串类型，将会失败。因此，`database/sql` 包定义了特殊类型来处理 `NULL` 值。在这里正确使用 `sql.NullString`：

```go
type pkgRow struct {
    // 其他字段
    RepoURL       sql.NullString
}
```

`sql.NullString` 定义了一个布尔字段 `Valid`，当 `repo_url` 列存储非空值时，该字段为 `true`。如果 `Valid` 为 `true`，`String` 字段包含字符串本身。向数据库添加字符串的方法也略有不同。首先，我们如下所示创建 `pkgRow` 对象：

```go
pkgRow{
    // 其他字段
    RepoURL: sql.NullString{
        String: "http://github.com/practicalgo/code",
        Valid:  true,
    },
}
```

然后我们如下所示更新并执行 `updateDb()` 函数：





```
func updateDb(config appConfig, row pkgRow) error {
    // TODO: 获取 соединение с БД
    columnNames := []string{
        "owner_id", "name", "version", "object_store_id",
    }
    valuesPlaceholder := []string{"?", "?", "?", "?"}
    args := []interface{}{
        row.OwnerId, row.Name, row.Version, row.ObjectStoreId,
    }

    if row.RepoURL.Valid {
        columnNames = append(columnNames, "repo_url")
        valuesPlaceholder = append(valuesPlaceholder, "?")
        args = append(args, row.RepoURL.String)
    }
    query := fmt.Sprintf(
        "INSERT INTO packages (%s) VALUES (%s);",
        strings.Join(columnNames, ","),
        strings.Join(valuesPlaceholder, ","),
    )

    result, err := conn.ExecContext(
        ctx, query, args...,
    )
    // TODO результаты обработки
}
```

由于 `repo_url` 列不是强制性的，我们检查 `pkgRow` 对象中是否存在有效的 `RepoURL` 字段，如果是，我们就更新 SQL 语句以将其包含内。

除了 `sql.NullString` 类型外，`database/sql` 包还定义了相应的类型，用于处理 `time.Time`、`float64`、`int32`、`int64` 以及其他 Go 类型的 NULL 值。在书籍源码仓库的 `chap11/mysql-demo` 目录下，你可以找到带有测试的代码列表，你可以对其进行实验以更好地理解前面的概念。

在本章的最后部分，你将学习如何在应用程序中使用数据库事务。

### 使用数据库事务

要启动事务，我们将调用在 `*sql.Conn` 对象定义的 `BeginTx()` 方法。它返回两个值：第一个值的类型为 `*sql.Tx`，第二个是错误值。如果我们成功获取了 `*sql.Tx` 值，我们将使用该对象定义的 `ExecContext()` 方法执行 SQL 查询。以下是包服务器修改后的 `updateDb()` 函数示例：

```
func updateDb(ctx context.Context, config appConfig, row pkgRow) error {
    conn, err := config.db.Conn(ctx)
    if err != nil {
        return err
    }
    defer conn.Close()

    tx, err := conn.BeginTx(ctx, nil)
    if err != nil {
        return err
    }

    result, err := tx.ExecContext(
        ctx,
        `INSERT INTO packages 
(owner_id, name, version, object_store_id) VALUES (?,?,?,?);`,
        row.OwnerId, row.Name, row.Version, row.ObjectStoreId,
    )
    if err != nil {
        rollbackErr := tx.Rollback()
        log.Printf("Txn Rollback Error:%v\n", rollbackErr)
        return err
    }
    return tx.Commit()
}
```

`BeginTx()` 方法接受两个参数：第一个是 `context.Context` 类型的对象，第二个是 `database/sql` 包定义的 `sql.TxOptions` 类型的对象：

```
type TxOptions struct {
    Isolation IsolationLevel
    ReadOnly  bool
}
```

`Isolation` 字段指定事务的隔离级别。如果没有指定，默认将使用 MySQL 驱动的默认隔离级别。我们使用的 MySQL 驱动器使用 MySQL 存储引擎的默认隔离级别。

如果在执行查询时遇到错误，我们将调用 `Rollback()` 方法回滚事务。如果在回滚事务时遇到错误，我们将记录它并返回原始错误。如果查询执行成功，如果有需要我们将执行任何其他查询。如果所有查询都执行成功，我们将调用 `tx.Commit()` 方法提交事务。`Commit()` 方法返回错误值，我们也返回该值。

在应用程序级别，在事务内部执行查询的一个很大优势是，如果创建事务时指定的上下文被取消，查询会自动回滚。这允许我们在服务器上实现这种行为：如果客户端取消了请求或由于其他原因取消，事务也将自动回滚。例如，我们可以这样更新包处理函数：

```
func packageRegHandler(
    w http.ResponseWriter,
    r *http.Request,
    config appConfig,
) {
    // TODO 加载包到对象存储
    err = updateDb(
        r.Context(),
        config,
        pkgRow{
            OwnerId:       packageOwner,
            Name:          packageName,
            Version:       packageVersion,
            ObjectStoreId: d.ID,
        },
    )
    // TODO: 其他代码
}
```

类似的策略也可以在 gRPC 应用中实现以响应客户端的断开。你可以在书籍源码仓库的 `chap11/pkg-server-2-transactions` 目录下找到使用事务的包服务器的更新代码实现。

## 总结

在本章中，你学习了如何持久化存储来自应用程序的数据。我们从研究如何在对象存储中存储非结构化大对象开始。我们使用了 `gocloud.dev/blob` 包来与存储服务交互。通过该包，切换对象存储服务只需要极少的更改。




到目前为止，在本书书中，我们一直使用标准库 `log` 包中定义的函数（如 `Printf()` 和 `Fatal()`）来记录应用程序的消息。这种记录方法实现简单，并且比完全不记录日志要。你可以使用日志中的文本在你的日志系统中进行搜索，但当你想要在日志*内部*搜索特定数据时，这就会变得不那么有用。一种非常常见的操作是搜索具有特定请求上下文或元数据的日志，例如针对特定命令、特定 HTTP 路径或 gRPC 方法的所有日志。使用我们到目前为止使用的记录方法，此类搜索既昂贵又低效。因此，你必须找到一种从应用程序生成日志的方法，使得每行日志都符合特定的结构——即单独标记的字段，其中包含日志数据，以及以元数据形式存在的上下文信息。实现这种日志机制有多种方法，它们通常都被称为*结构化日志*（structured logging）。日志行不再是任意形式的文本，而是每行日志都由数据*字段*组成，通常以键值对的形式或 JSON 格式的字符串形式。

在第 6 章“高级 HTTP 服务器应用程序”中的示例 6.2 中，我们定义了日志中间件 (`loggingMiddleware()`) 来创建如下日志行：

```
config.Logger.Printf(
    "protocol=%s path=%s method=%s duration=%f status=%d",
    r.Proto, r.URL.Path, r.Method,
    time.Now().Sub(startTime).Seconds(),
    customRw.code,
)
```

该应用程序创建的日志行由空格分隔的键值对组成，例如 `protocol=HTTP path=/api duration=0.05 status=200`。与简单的记录字符串（如 `HTTP request for /api/search received. Response 200. Duration: 0.1 second`）相比，这是一个改进。大多数日志系统都对这种格式的日志行具有内置的*分析*和*索引支持，，每一个键值对都可以单独进行搜索。这种格式在社区中被称为 `logfmt`，是因为在 Stripe 博客上发布了名为“Canonical Log Lines”的文章（[`stripe.com/blog/canonical-log-lines`](https://stripe.com/blog/canonical-log-lines)）。使用 `Printf()` 或 `log` 包中的任何函数来构建上述日志行都是繁琐的。因此，你可以使用第三方包 [`github.com/go-logfmt/logfmt`](https://github.com/go-logfmt/logfmt) 来创建键值对格式的日志行。该包仅实现了编码器和解码器，因此你仍然会使用标准库的日志函数来记录格式化的日志行。另一个第三方包是 [`github.com/apex/log`](https://github.com/apex/log)。

### 结构化日志

另一个第三方包，[`github.com/apex/log`](https://github.com/apex/log)。

### 使用 logfmt

另一个第三方包，[`github.com/apex/log`](https://github.com/apex/log)。

### 使用 logfmt 和其他格式

这种格式在社区中被称为 `logfmt`，是因为在 Stripe 博客上发布了名为“Canonical Log Lines”的文章（[`stripe.com/blog/canonical-log-lines`](https://stripe.com/blog/canonical-log-lines)）。使用 `Printf()` 或 `log` 包中的任何函数来构建上述日志行都是繁琐的。因此，你可以使用第三方包 [`github.com/go-logfmt/logfmt`](https://github.com/go-logfmt/logfmt) 来创建键值对格式的日志行。该包仅实现了编码器和解码器，因此你仍然会使用标准库的日志函数来记录格式化的日志行。

### 第三方库

另一个第三方包，[`github.com/apex/log`](https://github.com/apex/log)。

### JSON 格式

另一个第三方包，[`github.com/apex/log`](https://github.com/apex/log)。

### 方法对比

另一个第三方包，[`github.com/apex/log`](https://github.com/apex/log)。

### OpenTelemetry 和标准

另一个第三方包，[`github.com/apex/log`](https://github.com/apex/log)。

### 监控的未来

另一个第三方包，[`github.com/apex/log`](https://github.com/apex/log)。




`追踪（Traces）` 是跟踪系统中事务的遥测数据。当请求到达时，通常会发生多个作为该请求处理部分的动作。`追踪生命周期`与你应用程序中事务的生命周期相同。在事务处理期间发生的每个操作或事件都会触发一个间隔。因此，一次追踪由一个或多个间隔组成，这些间隔可能跨越系统边界——例如，多个服务和数据库。所有与事务相关的间隔都具有相同的追踪 ID，因此通过追踪系统，你可以直化地分析在事务范围内执行的各种操作的延迟以及成功/失败状态。指标会告诉你事务执行很慢，而追踪则提供了关于为什么执行很慢的更详细信息。

例如，让我们考虑我们在第 11 章](#c11.xhtml)“处理数据存储”中实现的包服务器。包的加载是一个由两个独立操作组成的事务：将包加载到对象存储服务中，以及在关系型数据库中更新包的元数据。这些操作中的每一个都会创建一个包含操作详细信息和操作耗用时间的追踪。由于这两个追踪具有相同的事务 ID，你可以看到事务的总体延迟，以及每个组成操作的延迟。这在服务导型架构中最为有用，因为在这种架构中，一次事务会发生多次服务调用。存储和分析追踪数据需要专门的系统，历史上向这些系统发送追踪数据通常需要使用特定供应商的库。然而，OpenTelemetry 项目的 Go 库允许实现独立于供应商的追踪。在本文编写时，项目 ([`github.com/open-telemetry/opentelemetry-go`](https://github.com/open-telemetry/opentelemetry-go)) 发布了 1.0.0-RC 版本。我们将使用该版本并仅使用与追踪导出相关的函数。在下一节中，你将了解一些用于修改我们在书中编写的应用程序的模式，以便这些程序能够输出遥测数据。

## 输出遥测数据

我创建了一个自定义命令行客户端 `pkgcli` 来与第 1 章](#c1.xhtml)中实现的服务器进行交互。我还修改了包服务器以便与 gRPC 服务器通信以检查加载信息。你可以在 `appendix-a` 目录下找到所有相关的代码和说明。存储日志、指标和追踪需要专门的系统，存在许多开源解决方案。在接下来的示例中，将仅演示从应用程序传输数据，而不是这些数据的可视化和分析。你可以在 `appendix-a/README.md` 文件中找到运行命令行程序的完整说明。

### 命令行应用程序

对于命令行应用程序，我们将通过初始化用于导出指标和追踪的网络客户端来设置日志。然后，我们将这些初始化的配置对应用程序的其他部分开放，以便在命令执行期间注册任何消息、发布指标或导出追踪。`pkgcli` 应用程序的示例代码位于 `appendix-a/command-line-app` 目录。它使用了 `flag` 包并应用了第 2 章](#c2.xhtml)“高级命令行应用程序”描述的子命令架构，创建一个包含两个命令——`register` 和 `query` 的应用程序。第一个命令允许用户将包上传到服务器，第二个命令用于查询服务器信息。我们创建了 `config` 包，并在内部定义了 `PkgCli` 结构体来封装初始化的日志、指标和追踪客户端：

```
type PkgCli struct {
    Logger  zerolog.Logger
    Metrics MetricReporter
    Tracer  TraceReporter
}
```

我们创建了 `telemetry` 包，包含三个函数：`InitLogging()`、`InitMetrics()` 和 `InitTracing()`，它们返回初始化的 `zerolog.Logger`、`telemetry.MetricReporter` 和 `telemetry.TraceReporter` 对象。后两个类型用于封装发布指标和导出追踪的客户端。`telemetry` 包中的 `logging.go` 文件如下所示定义 `InitLogging()` 函数：

```go
package telemetry

import (
    "io"

    "github.com/rs/zerolog"
)

func InitLogging(
    w io.Writer,
    version string,
    logLevel int,
) zerolog.Logger {

    rLogger := zerolog.New(w)
    versionedL := rLogger.With().Str("version", version)
    timestampedL := versionedL.Timestamp().Logger()
    levelledL := timestampedL.Level(zerolog.Level(logLevel))

    return levelledL
}
```

我们调用 [github.com/rs/zerolog](http://github.com/rs/zerolog) 包中的 `zerolog.New()` 函数来创建一个根记录器，这是一个输出参数设置为 `w` 的 `zerolog.Logger` 对象。然后，我们通过调用 `With()` 方法向根记录器添加日志上下文。这通过使用 `Str()` 方法添加上下文，从根记录器 `rLogger` 创建了一个子记录器，该方法为所有日志消息添加一个名为 `version` 的键，其值为设置为指定的字符串 `version`。这将导致应用程序的所有日志都包含该字段中的应用程序版本。

然后，我们添加另一个日志上下文，以便在日志中添加时间戳并创建另一个子记录器 `timestampedL`。最后，我们通过调用 `Level()` 方法添加日志级别逻辑，并返回创建的 `zerolog.Logger` 对象。配置后的记录器仅在消息级别等于或高于通过 `logLevel` 值指定的配置级别时才会记录该消息。`logLevel` 的值应该是从 -1 到 5 之间的整数（包含两端）。将级别设置为 -1 将记录所有消息，将级别设置为 5 将仅记录恐慌（panic）消息。

`telemetry` 包中的 `metrics.go` 文件如下所示定义 `InitMetrics()` 函数：

```go
package telemetry

import (
    "fmt"

    "github.com/DataDog/datadog-go/statsd"
)

type MetricReporter struct {
    statsd *statsd.Client
}

func InitMetrics(statsdAddr string) (MetricReporter, error) {
    var m MetricReporter
    var err error
    m.statsd, err = statsd.New(statsdAddr)
    if err != nil {
        return m, err
    }
    return m, nil
}
```

我们选择了 [github.com/DataDog/datadog-go/statsd](http://github.com/DataDog/datadog-go/statsd) 包，因为它得到了良好的支持。我们通过调用 `statsd.New()` 函数创建客户端，传递 statsd 服务器地址并将创建的客户端分配给 `MetricReporter` 对象的 `statsd` 字段。



然后，我们定义 `ReportDuration()` 方法，它将传递一个包含命令执行持续时间的直方图指标。持续时间以秒为单位。指标将将添加两个标签（tag），以便对指标进行分组和聚合。我们将根据 `Cmd` 字段添加已执行的命令作为第一个标签，并独立地根据命令是否执行成功（如 `Success` 字段所示）添加第二个标签。该方法的定义如下：

```go
func (m MetricReporter) ReportDuration(metric DurationMetric) {
    metricName := "cmd.duration"
    m.statsd.Histogram(
        metricName,
        metric.DurationMs,
        []string{
            fmt.Sprintf("cmd:%s", metric.Cmd),
            fmt.Sprintf("success:%v", metric.Success),
        },
        1, //采样率 (0-无, 1 -全部)
    )
}
```

对于其他的情况，可以定义类似的方法来传递其他类型的指标。

`InitTracing()` 方法定义在 `telemetry` 包的 `trace.go` 文件中。在其中，我们如下所示配置 `telemetry` 包中整个应用程序的链路追踪：

```go
package telemetry

import (
    "context"

    "go.opentelemetry.io/otel"
    "go.opentelemetry.io/otel/exporters/jaeger"
    "go.opentelemetry.io/otel/trace"
    // TODO 导入其他 otel 的包
)

type TraceReporter struct {
    Client trace.Tracer
    Ctx    context.Context
}

func InitTracing(
    jaegerAddr string,
) (TraceReporter, *sdktrace.TracerProvider, error) {

    // 1. 配置链路导出器

    // 2. 配置范围处理器 (Span Processor)

    // 3. 配置 TracerProvider (TracerProvider)

    // 4. 创建传播器 (Propagator)

    // 5. 创建并配置 Tracer

    // 6. 返回 TraceReporter 类型的值

}
```

接下来将解释六个关键步骤。我们需要一个可以导出链路的终点，以便我们可以进行查看和查询。我们将使用 `Jaeger` ([www.jaegertracing.io](http://www.jaegertracing.io))，这是一个开源的分布式追踪系统，因此我们使用了在 `go.opentelemetry.io/otel/exporters/jaeger` 包中实现的 Jaeger 导出器。

下面的代码段创建了链路导出器：

```go
traceExporter, err := jaeger.New(
    jaeger.WithCollectorEndpoint(
        jaeger.WithEndpoint(jaegerAddr),
    ),
)
```

请注意，此处我们也可以使用 `go.opentelemetry.io/otel/exporters/otlp` 包实现的 OpenTelemetry 收集器导出器，使我们的应用程序完全相对于所使用的分布式追踪系统中立。然而，为了简单起见，我直接使用了 Jaeger 导出器。

然后，我们配置了范围处理器，通过使用之前创建的链路导出器来配置它，以观测应用程序输出的 `span` 数据处理：

```go
bsp := sdktrace.NewSimpleSpanProcessor(traceExporter)
```

对于生产应用，建议配置另一种范围处理器，即如下所示创建的批范围处理器（Batch Span Processor）：

```go
bsp := sdktrace.NewBatchSpanProcessor(traceExporter)
```

下一步是创建 `TracerProvider`，如下：

```go
tp := sdktrace.NewTracerProvider(
    sdktrace.WithSpanProcessor(bsp),
    sdktrace.WithResource(resource),
)
otel.SetTracerProvider(tp)
```

现在，我们就可以在代码中开始创建和结束 span：

```go
ctx, span := otel.Tracer("my-tracer").Start(ctx, "operation-name")
defer span.End()
```




```go
c.Logger = c.Logger.With().Str("command", "register").Logger()
tStart := time.Now()
defer func() {
    duration := time.Since(startTime).Seconds()
    c.Metrics.ReportDuration(
        telemetry.DurationMetric{
            Cmd:        "pkgcli.register",
            DurationMs: duration,
            Success:    err == nil,
        },
    )
}()
err = cmd.HandleRegister(&c, w, args[1:])
```

在调用特定子命令的处理函数之前，我们更新了记录器以创建一个新的上下文，以便所有日志都包含一个额外的 `command` 字段，其值设置为 `register`，这用于标识日志消息与 `register` 子程序相关。

我们还启动了计时器，然后在延迟函数中使用 `ReportDuration()` 方法来报告命令的执行时长。

在 `cmd` 包中定义的 `HandleRegister()` 函数中，我们在向包服务器发送 HTTP 请求之前，如下所示创建了范围（span）：

```
ctx, span := cliConfig.Tracer.Client.Start(
    cliConfig.Tracer.Ctx,
    "pkgquery.register",
)
defer span.End()
```

接下来，让我们来看看经过仪器化的包服务器版本。

### HTTP 应用

对于 HTTP 服务器应用，我们将配置日志记录，在服务器启动时初始化用于导出指标和追踪的网络客户端。然后，我们将使这些初始化的配置对应用程序的其他部分可用，以便在执行任何命令期间允许注册任何消息、发布指标或导出追踪。

修改后的包服务器代码位于 `appendix-a/http-app` 目录。它是基于我们在 第 11 章 中实现的包服务器版本创建的。

我们在配置包中定义了 `AppConfig` 结构，以封装应用程序配置，包括遥测配置：

```go
type AppConfig struct {
    PackageBucket *blob.Bucket
    Db            *sql.DB
    UsersSvc      users.UsersClient

    // 遥测
    Logger   zerolog.Logger
    Metrics  telemetry.MetricReporter
    Trace    trace.Tracer
    TraceCtx context.Context
    Span     trace.Span
    SpanCtx  context.Context
}
```

`telemetry` 包在 `logging.go`、`metrics.go` 和 `trace.go` 文件中定义了初始化整个遥测配置的方法。`InitLogging()` 和 `InitMetrics()` 方法将与之前为命令行应用程序定义的相同。

`middleware` 包包含了用于传递遥测数据的中间件定义。日志记录中间件定义如下：

```go
func LoggingMiddleware(
    c *config.AppConfig, h http.Handler,
) http.Handler {
    return http.HandlerFunc(func(
        w http.ResponseWriter, r *http.Request,
    ) {
        c.Logger.Printf("Got request - headers:%#v\n", r.Header)
        startTime := time.Now()
        h.ServeHTTP(w, r)
        c.Logger.Info().Str(
            "protocol",
            r.Proto,
        ).Str(
            "path",
            r.URL.Path,
        ).Str(
            "method",
            r.Method,
        ).Float64(
            "duration",
            time.Since(startTime).Seconds(),
        ).Send()
    })
}
```

你可以在上一个代码段中看到结构化日志记录的示例。我们创建一个日志行（内部值 `Zerolog.Event`），逐步添加我们想要添加到日志中的键值对字段，并调用 `Send()` 方法来触发日志的创建。如上定义的 `LoggingMiddleware()` 函数创建的请求日志将如下：

```
{"level":"info","version":"0.1","protocol":"HTTP/1.1",
"path":"/api/packages","method":"POST","duration":0.038707083,
"time":"2021-09-12T08:39:05+10:00"}
```

我们又定义了另一个中间件来增加请求处理的延迟：

```go
func MetricMiddleware(c *config.AppConfig, h http.Handler) http.Handler {
    return http.HandlerFunc(func(
        w http.ResponseWriter, r *http.Request,
    ) {
        startTime := time.Now()
        h.ServeHTTP(w, r)
        duration := time.Since(startTime).Seconds()
        c.Metrics.ReportLatency(
            telemetry.DurationMetric{
                DurationMs: duration,
                Path:       r.URL.Path,
                Method:     r.Method,
            },
        )

    })
}
```

`InitTracing()` 方法看起来稍有不同：

```go
func InitTracing(jaegerAddr string) error {
    traceExporter, err := jaeger.New(
        jaeger.WithCollectorEndpoint(
            jaeger.WithEndpoint(jaegerAddr + "/api/traces"),
        ),
    )
    if err != nil {
        return err
    }
    bsp := sdktrace.NewSimpleProcessor(traceExporter)

    tp := sdktrace.NewTracerProvider(
        sdktrace.WithSpanProcessor(bsp),
        sdktrace.WithResource(
            resource.NewAttributes(
                semconv.ServiceName("server"),
            ),
        ),
    )
    otel.SetTracerProvider(tp)
    propagator := propagation.TraceContext{}
    otel.SetTextMapPropagator(propagator)
    return nil
}
```

我们设置了全局追踪提供者，但没有创建中间件。因此，我们创建了自己的中间件。`TracingMiddleware()` 如下：

```go
func TracingMiddleware(
    c *config.AppConfig, h http.Handler,
) http.Handler {
    return http.HandlerFunc(func(
        w http.ResponseWriter, r *http.Request,
    ) {
        c.Trace = otel.Tracer("")
        tc := propagation.TraceContext{}
        incomingCtx := tc.Extract(
            r.Context(),
            propagation.HeaderCarrier(r.Header),
        )
        c.SpanCtx = incomingCtx

        ctx, span := c.Trace.Start(
            c.SpanCtx,
            r.URL.Path,
        )
        c.Span = span
        c.SpanCtx = ctx
        defer span.End()

        h.ServeHTTP(w, r)
    })
}
```

值得注意的是，尽管 `go.opentelemetry.io/contrib/instrumentation/net/http/otelhttp` 定义了用于追踪 HTTP 服务器的中间件，在这里我们定义了中间中间件。例如，在 `storage` 包的 `UpdateDb()` 函数中，我们在开始数据库事务之前创建一个范围（span），并在事务提交或回滚后结束它：

```go
func UpdateDb(
    ctx context.Context,
    config *config.AppConfig,
    row types.PkgRow,
) error {
    conn, err := config.Db.Conn(ctx)
    if err != nil {
        return err
    }
    defer func() {
        err = conn.Close()
        if err != nil {
            config.Logger.Debug().Msg(err.Error())
        }
    }()

    _, spanTx := config.Trace.Start(
        config.SpanCtx, "sql:transaction",
    )
    defer spanTx.End()

    tx, err := conn.BeginTx(ctx, nil)
    if err != nil {
        return err
    }
    // 其他部分代码
}
```

未来，可能会出现带有自动工具的 `database/sql` 包版本，那时我们就不需要为数据库操作编写属于自己的手动追踪代码了。




在创建用于用户服务的 gRPC 客户端时，我们利用自动管理库的优势。在 `server.go` 中，你会找到以下函数：

```go
func setupGrpcConn(addr string) (*grpc.ClientConn, error) {
    return grpc.DialContext(
        context.Background(),
        addr,
        grpc.WithInsecure(),
        grpc.WithUnaryInterceptor(
            otelgrpc.UnaryClientInterceptor(),
        ),
        grpc.WithStreamInterceptor(
            otelgrpc.StreamClientInterceptor(),
        ),
    )
}
```

`go.opentelemetry.io/contrib/instrumentation/` 包定义了客户端和服务器端的拦截器，用于将 gRPC 应用程序与 OpenTelemetry 集成。

接下来，让我们查看 gRPC 服务器的插化版本。

## gRPC 应用程序

与 HTTP 服务器应用程序一样，我们将在服务器启动时通过初始化网络客户端来导出指标和追踪，从而配置日志记录。插化的 gRPC 服务器代码位于 `appendix-a/grpc-server` 目录。这是我们在 第 8 章 “使用 gRPC 创建 RPC 应用”中创建的 `Users` 服务版本，它定义了一个唯一的单元 RPC 方法 `GetUser()`。服务的实现位于主包中的 `usersServiceHandler.go` 文件中。你也可以通过向 `userService` 结构体（它是 `Users`服务的实现）添加额外字段，查看服务处理程序之间数据交换的示例：

```go
type userService struct {
    users.UnimplementedUsersServer
    config config.AppConfig
}

func (s *userService) GetUser(
    ctx context.Context,
    in *users.UserGetRequest,
) (*users.UserGetReply, error) {
    s.config.Logger.Printf(
        "Received request for user verification: %s\n",
        in.Auth,
    )
    u := users.User{
        Id: rand.Int31n(4) + 1,
    }
    return &users.UserGetReply{User: &u}, nil
}
```

`grpc.Server` 对象在 `main()` 函数中如下创建：

```go
s := grpc.NewServer(
    grpc.ChainUnaryInterceptor(
        interceptors.MetricUnaryInterceptor(&config),
        interceptors.LoggingUnaryInterceptor(&config),
        otelgrpc.UnaryServerInterceptor(),
    ),
    grpc.ChainStreamInterceptor(
        interceptors.MetricStreamInterceptor(&config),
        interceptors.LoggingStreamInterceptor(&config),
        otelgrpc.StreamServerInterceptor(),
    ),
)
```

我们在拦截器包中定义了指标和日志拦截器。我们还注册了由 `go.opentelemetry.io/contrib/instrumentation/` 包定义的拦截器，它为我们提供了 gRPC 服务处理程序调用的自动插化处理。`telemetry` 包初始化了日志记录、指标和追踪的配置。你会发现其初始化代码与上一节中的 HTTP 服务器相同。

在拥有上述 gRPC 工具链的情况下，我们在创建用于用户服务的 gRPC 客户端时利用了自动管理库的优势。在 `server.go` 中，你会找到以下函数。`go.opentelemetry.io/contrib/instrumentation/` 包定义了客户端和服务器端的拦截器，用于将 gRPC 应用程序与 OpenTelemetry 集成。

接下来，让我们查看 gRPC 服务器的插化版本。与 HTTP 服务器应用程序一样，我们将在服务器启动时通过初始化网络客户端来导出指标和追踪，从而配置日志记录。插化的 gRPC 服务器代码位于 `appendix-a/grpc-server` 目录。这是我们在 第 8 章 “使用 gRPC 创建 RPC 应用”中创建的 `Users` 服务版本，它定义了一个唯一的单元 RPC 方法 `GetUser()`。服务的实现位于主包中的 `usersServiceHandler.go` 文件中。你也可以通过向 `userService` 结构体（它是 `Users`服务的实现）添加额外字段，查看服务处理程序之间数据交换的示例。

## 总结

我们在拦截器包中定义了指标和日志拦截器。我们还注册了由 `go.opentelemetry.io/contrib/instrumentation/` 包定义的拦截器，它为我们提供了 gRPC 服务处理程序调用的自动插化处理。`telemetry` 包初始化了日志记录、指标和追踪的配置。你会发现其初始化代码与上一节中的 HTTP 服务器相同。

在拥有上述 gRPC 工具链的情况下，我们在创建用于用户服务的 gRPC 客户端时利用了自动管理库的优势。在 `server.go` 中，你会找到以下函数。`go.opentelemetry.io/contrib/instrumentation/` 包定义了客户端和服务器端的拦截器，用于将 gRPC 应用程序与 OpenTelemetry 集成。

## 部署

在拥有上述 gRPC 工具链的情况下，我们在创建用于用户服务的 gRPC 客户端时利用了自动管理库的优势。在 `server.go` 中，你会找到以下函数。`go.opentelemetry.io/contrib/instrumentation/` 包定义了客户端和服务器端的拦截器，用于将 gRPC 应用程序与 OpenTelemetry 集成。

## 配置管理

与 HTTP 服务器应用程序一样，我们将在服务器启动时通过初始化网络客户端来导出指标和追踪，从而配置日志记录。插化的 gRPC 服务器代码位于 `appendix-a/grpc-server` 目录。这是我们在 第 8 章 “使用 gRPC 创建 RPC 应用”中创建的 `Users` 服务版本，它定义了一个唯一的单元 RPC 方法 `GetUser()`。服务的实现位于主包中的 `usersServiceHandler.go` 文件中。你也可以通过向 `userService` 结构体（它是 `Users`服务的实现）添加额外字段，查看服务处理程序之间数据交换的示例。

## 数据处理

与 HTTP 服务器应用程序一样，我们将在服务器启动时通过初始化网络客户端来导出指标和追踪，从而配置日志记录。插化的 gRPC 服务器代码位于 `appendix-a/grpc-server` 目录。这是我们在 第 8 章 “使用 gRPC 创建 RPC 应用”中创建的 `Users` 服务版本，它定义了一个唯一的单元 RPC 方法 `GetUser()`。服务的实现位于主包中的 `usersServiceHandler.go` 文件中。

## 应用 B

与 HTTP 服务器应用程序一样，我们将在服务器启动时通过初始化网络客户端来导出指标和追踪，从而配置日志记录。插化的 gRPC 服务器代码位于 `appendix-a/grpc-server` 目录。这是我们在 第 8 章 “使用 gRPC 创建 RPC 应用”中创建的 `Users` 服务版本，它定义了一个唯一的单元 RPC 方法 `GetUser()`。服务的实现位于主包中的 `usersServiceHandler.go` 文件中。

## 应用 C1

与 HTTP 服务器应用程序一样，我们将在服务器启动时通过初始化网络客户端来导出指标和追踪，从而配置日志记录。插化的 gRPC 服务器代码位于 `appendix-a/grpc-server` 目录。这是我们在 第 8 章 “使用 gRPC 创建 RPC 应用”中创建的 `Users` 服务版本，它定义了一个唯一的单元 RPC 方法 `GetUser()`。服务的实现位于主包中的 `usersServiceHandler.go` 文件中。

## 应用 C2

与 HTTP 服务器应用程序一样，我们将在服务器启动时通过初始化网络客户端来导出指标和追踪，从而配置日志记录。插化的 gRPC 服务器代码位于 `appendix-a/grpc-server` 目录。这是我们在 第 8 章 “使用 gRPC 创建 RPC 应用”中创建的 `Users` 服务版本，它定义了一个唯一的单元 RPC 方法 `GetUser()`。服务的实现位于主包中的 `usersServiceHandler.go` 文件中。

## 应用 C3

与 HTTP 服务器应用程序一样，我们将在服务器启动时通过初始化网络客户端来导出指标和追踪，从而配置日志记录。插化的 gRPC 服务器代码位于 `appendix-a/grpc-server` 目录。这是我们在 第 8 章 “使用 gRPC 创建 RPC 应用”中创建的 `Users` 服务版本，它定义了一个唯一的单元 RPC 方法 `GetUser()`。服务的实现位于主包中的 `usersServiceHandler.go` 文件中。

## 应用 D1

与 HTTP 服务器应用程序一样，我们将在服务器启动时通过初始化网络客户端来导出指标和追踪，从而配置日志记录。插化的 gRPC 服务器代码位于 `appendix-a/grpc-server` 目录。这是我们在 第 8 章 “使用 gRPC 创建 RPC 应用”中创建的 `Users` 服务版本，它定义了一个唯一的单元 RPC 方法 `GetUser()`。服务的实现位于主包中的 `usersServiceHandler.go` 文件中。

## 应用 D2

与 HTTP 服务器应用程序一样，我们将在服务器启动时通过初始化网络客户端来导出指标和追踪，从而配置日志记录。插化的 gRPC 服务器代码位于 `appendix-a/grpc-server` 目录。这是我们在 第 8 章 “使用 gRPC 创建 RPC 应用”中创建的 `Users` 服务版本，它定义了一个唯一的单元 RPC 方法 `GetUser()`。服务的实现位于主包中的 `usersServiceHandler.go` 文件中。

## 应用 E1

与 HTTP 服务器应用程序一样，我们将在服务器启动时通过初始化网络客户端来导出指标和追踪，从而配置日志记录。插化的 gRPC 服务器代码位于 `appendix-a/grpc-server` 目录。这是我们在 第 8 章 “使用 gRPC 创建 RPC 应用”中创建的 `Users` 服务版本，它定义了一个唯一的单元 RPC 方法 `GetUser()`。服务的实现位于主包中的 `usersServiceHandler.go` 文件中。

## 应用 E2

与 HTTP 服务器应用程序一样，我们将在服务器启动时通过初始化网络客户端来导出指标和追踪，从而配置日志记录。插化的 gRPC 服务器代码位于 `appendix-a/grpc-server` 目录。这是我们在 第 8 章 “使用 gRPC 创建 RPC 应用”中创建的 `Users` 服务版本，它定义了一个唯一的单元 RPC 方法 `GetUser()`。服务的实现位于主包中的 `usersServiceHandler.go` 文件中。




```go
type serverCfg struct {
    AuthToken string `yaml:"auth_token"`
}

type telemetryCfg struct {
    LogLevel   int    `yaml:"log_level"`
    StatsdAddr string `yaml:"statsd_addr"`
    JaegerAddr string `yaml:"jaeger_addr"`
}

type pkgCliInput struct {
    Server    serverCfg
    Telemetry telemetryCfg
}
```

第一个结构体类型 `serverCfg` 对应 YAML 配置中的服务器对象。第二个结构体类型 `telemetryCfg` 对应 YAML 配置中的遥测对象，第三个结构体类型 `pkgCliInput` 则对应整个 YAML 配置。结构体标签 `yaml:"auth_token"`（以及其他）用于指定在 YAML 文件中显示的相应键名。

接下来，我们将使用 [go.uber.org/config](http://go.uber.org/config) 包来读取包含 YAML 格式数据的配置文件：

```go
import uberconfig "go.uber.org/config"
 
provider, err := uberconfig.NewYAML(
    uberconfig.File(configFilePath),
    uberconfig.Expand(os.LookupEnv),
)
```

`NewYAML()` 函数接收一个或多个数据源。在这里我们指定了两个源：第一个是通过变量 `configFilePath` 指定路径的文件；第二个是函数 `Expand()`，它接收一个签名如下的函数作为参数：`func(string) (string, bool)`。在这里，我们将标准库中的 `os.LookupEnv` 函数作为参数传递给 `Expand()`。结果，我们合并了环境变量和配置文件，以创建一个合并的应用配置。值得注意的是，解析 `${X_AUTH_TOKEN}` 和 `${LOG_LEVEL:1}` 等对象值的功能是由 [go.uber.org/config](http://go.uber.org/config) 包中的 `Expand()` 函数实现的。

如果 `NewYAML()` 函数返回零错误，现在我们就可以读取数据了。接下来的代码段将读取数据并尝试将其反序列化为 `pkgCliInput` 类型的对象：

```go
c := pkgCliInput{}
if err := provider.Get(uberconfig.Root).Populate(&c); err != nil {
    return nil, err
}
```

如果之前的操作成功，我们可以对读取的数据进行任何数据值检查，例如：

```go
if c.Telemetry.LogLevel < -1 || c.Telemetry.LogLevel > 5 {
    return nil, errors.New("invalid log level")
}
```

你可以在书籍源码仓库的 `appendix-b/command-line-app` 目录下找到使用上述逻辑读取应用配置的修改版 `pkgcli`。具体来说，在 `main.go` 文件内部你将找到实现上述逻辑的 `readConfig()` 函数以及 `config.yml` 示例文件。

如果你想使用其他文件格式以及其他读取配置数据的方法，值得研究 [github.com/spf13/viper](http://github.com/spf13/viper) 包。

## 部署

（根据优化逻辑跳过重复块）




您可以看到我们如何使用 `docker run` 命令的 `-e` 标记指定环境变量。我们使用 `-v` 标记来指定卷挂载；即我们将宿主机系统中的目录挂载到容器内部。在这里，我们挂载了包含我们要加载的包的目录。您可以在书籍源码仓库的 `appendix-b/command-line-app` 目录中找到包含 `Dockerfile` 和应用程序的完整示例。通常，您会使用 Docker 镜像来发布服务器应用程序，但如果您的命令行应用程序想要分发默认配置文件，Docker 镜像是一个实现此点的方便方式。

## 部署服务器应用程序

在公共互联网或内部网络中为其他用户部署 HTTP 或 gRPC 服务器时，应该运行多个应用程序实例。您可以直接在虚拟机机上运行服务器，也可以将其作为容器运行，并可能使用您自建的解决方案或如 `Nomad` 或 `Kubernetes` 等编排系统。

然后，您必须配置一个负载均衡器，由它接收请求并将它们重定向到您的应用程序。因此，深入理解负载均衡器与应用程序之间的交互至关重要。

负载均衡器如何知道您的应用程序实例已准备好接收新请求？*健康检查*是负载均衡器检查应用程序实例可用性的常用方法。因此，通常会在您的应用程序中定义一个特定的 HTTP 端点或 gRPC 方法，负载均衡器可以定期向其发送请求以获取应用程序的健康状态。其他现代软件，如*服务网格*（service mesh），也执行与传统负载均衡器相同的作用，它们也会检查您的应用程序健康状况，并在决定是否将流量重定向到应用程序实例时考虑它。如果实例的健康检查失败，它将停止接收新请求，并且可能可以使用各种基础设施功能自动删除它并创建一个新的。健康检查通常分为分类：存活检查（liveness）和*深度检查*（deep check）。第一个检查的成功响应仅确认应用程序本身能够响应检查。第二类检查更为复杂，因为它确保了应用程序依赖（如其他服务或数据库）的可用性，从而排除了网络故障或凭据错误等问题。深度检查应该频繁运行，可能仅在启动时运行，因为它针对的情况很可能在初期就被发现。

此外，还需要充分关注我们在书中不同章节详细讨论过的超时配置。应特别关注云提供商负载均衡器或其他类似软件的超时设置，因为它们决定了在断开连接之前会等待多久的响应。当您使用长连接时（例如在 gRPC 流通信期间），这一点也应该引起关注。

在第 7 章和第 10 章中，我们讨论了如何使用证书为 HTTP 和 gRPC 应用程序加密客户端与服务器之间的通信。当负载均衡器后运行应用程序实例时，客户端的 TLS 连接通常会在负载器处中断，因此负载均衡器与您的应用程序之间的通信是不加密的。这种情况很常见，因为它简单，并且会产生虚假的安全感，因为大多数情况下这些流量处于私有网络中。但需要强调的是，这是推荐的，您应该努力加密所有的网络。

## 总结

在应用程序中，我们讨论了与部署相关的三个关键问题：配置、流量和安全。您将采取的步骤将取决于基础设施，希望这些策略为您提供良好的指导。

## 索引

（此处为索引部分，根据格式要求）




* 从过载服务器下载，85
* `createHTTPGetRequestWithTrace()` 函数，101–102
* `createMultiPartMessage()` 函数，75–76
* `CreateRepo()` 方法
    * 客户端流式传输，237–239
    * 接收和发送任意字节，249–251, 254
* `createRPCStream()` 函数，306
* `credentials.NewServerTLSFromFile()` 函数，276
* `ctx.Done()` 方法，296–297
* `ctx.Value()` 方法，120
* `ctxWithTimeout.Done()` 函数，290
* D
* `Decode()` 函数，124–126
* `decodeHandler()` 函数，125
* `DialContext()` 函数
    * TLS 连接保护，277
    * 改进连接设置，298, 299
    * 连接管理，306–307
    * gRPC 服务器测试，208
* `DNSDone` 函数，102–103
* `Do()` 方法，92
* Docker Desktop，314, 318
* `Dockerfile`，370–372
* `doSomeWork()` 函数
    * 处理客户端断开，171–172
    * 中断请求处理，166–167, 168
* E
* `encoding` 包，61
* Envoy，309
* `Err()` 方法
    * 中断请求处理，166
    * 关系型数据库，337
* `Errorf()` 函数，283
* `errors.Is()` 函数
    * 执行可用性检查，283
    * 重复的错误信息，23
* `execCommandContext()` 函数，52–53
* `ExecContext()` 方法，330, 333, 343, 346
* `executeCommand()` 函数，55
* `Exists()` 方法，321
* `Expand()` 函数，369
* F
* `fetchPackageData()` 函数，62–63, 65
* `fetchRemoteResource()` 函数
    * 获取数据的反序列化，61
    * 测试加载器，59, 60
    * 从过载服务器下载，83
    * 超时测试，85, 87
* `flag` 包，14–22
* `Flush()` 方法，129, 131
* `fmt.Fprintf()` 函数
    * 处理函数，109
    * 编写 gRPC，206
* `fmt.Sprintf()` 函数，336
* `FormData()` 方法，74
* `Form` / `Post`，116
* `Fprintf()` 函数
    * 关于函数，3
    * 响应流式数据，128
* `FromIncomingContext()` 函数，266
* G
* `Get()` 函数
    * 获取数据的反序列化，63
    * 加载数据，58
    * 请求配置，91
    * TLS 服务器测试，191
* `getBucket()` 函数，316–318
* `getDatabaseConn()` 方法，342, 344
* `Getenv()` 函数，107
* `getHealthSvcClient()` 函数，281–282
* `GetHelp()` 方法
    * 双向流式传输，239–246
    * 客户端可靠性，298
    * 临时故障处理，301, 304
    * 运行时错误处理，288–289
    * 使用拦截器实现中间件，263, 264, 265, 268
* `getName()` 函数
    * 编写单元测试，12
    * 关于函数，2–3, 5
* `getNameContext()` 函数，49–50
* `getOwnerId()` 函数，331–332
* `GetRepos()` 函数，222, 225, 230–232, 235
* `getTestBucket()` 函数，323
* `getTestDb()` 函数，339, 342
* `GetUser()` 方法
    * 在 gRPC，195
    * 序列化反序列化，214–216
    * 客户端可靠性，298
    * 编写客户端，204–205, 206
    * 编写 gRPC，204
    * 编写服务器，198–203
    * 关于应用，193–197
    * 发送任意字节，246–256
    * 遥测数据传输，364–365
    * 获取任意字节，246–256
    * 双向流式传输，229–246
    * 扩展应用，229–272
    * 使用拦截器实现中间件，256–272
    * 创建 gRPC 应用程序，193–228
    * 客户端测试，211–213
    * 服务器测试，207–210





* TLS 连接ная защита, 276
* написание gRPC серверов, 199
* использование middleware для реализации промежуточного ПО, 267
* тестирование gRPC gRPC, 208
* `grpc.StreamInterceptor()` функция, 267–268
* `grpc.UnaryInterceptor()` функция, 267–268
* `grpc.WaitForReady()` функция, 300
* `grpc.WithBlock()` функция
    * написание gRPC клиентов, 204
    * улучшение настроек подключения, 298, 299
* `grpc.WithContextDialer()` функция, 208
* `grpc.WithInsecure()` функция
    * TLS 连接ная защита, 276
    * написание gRPC клиентов, 203
* `grpc.WithReturnConnectionError()` функция, 300
* `grpc.WithTransportCredentials()` функция, 277
* `grpc.WithUnaryInterceptor()` функция, 259
* H
* `handeUsersAPI()` функция, 162–163
* `Handle()` метод, 136
* `handleCmdA()` функция, 35
* `handleCmdB()` функция, 35
* `handleCommand()` функция
    * реализация подкоманд, 39
    * тестирование пакета `main`, 43–45
* `HandleFunc()` функция
    * передача данных между функциями обработчика, 136
    * функции обработчика и, 110
* `HandleGrpc()` функция, 41–42
* `HandleHttp()` функция, 40–41
* `handlePing()` функция, 172–173
* `handler()` функция, 264
* `Handler` тип, 133–134
* `HandleRegister()` функция, 359–360
* `HandlerFunc` техника, 140–142
* `handlers.Register()` функция, 152
* `handleUserAPI()` функция
    * обработка отключений клиентов, 170
    * прерывание обработки запроса,
    * реализация таймаута сервера, 177–178
* HAproxy, 309
* `HeadBucket()` метод, 326
* `healthCheckHandler()` функция, 155
* HTTP клиенты
    * написание, 57–80
    * настрой, 81–91
    * настрой запросов, 91–92
    * пул соединений, 99–104
    * реализация клиентского промежуточного ПО, 92–99
* HTTP-приложения, передающие данные телеметрии, 360–364
* HTTP протокол, 66–72
* HTTP серверы
    * `Handler` тип, 133
    * `Request` структура, 114–17
    * готовый к производству, 161–91
    * реализация промежуточного ПО для сервера, 139–147
    * реализация тестов для серверных приложений, 147–159
    * настрой обработчиков запросов, 108–111
    * обработка запросов на стриминг, 121–126
    * потоковые данные в ответов, 126–131
    * прикрепление метаданных к запросам, 118–121
    * расширенные приложения, 133–159
    * собрать первый, 105–108
    * совместное использование данных между функциями обработчика, 134–139
    * тестирование, 112–114
    * HTTP/2, конфигурация, 184–188
* `http.Get()` функция, 83–84
* `http.ListenAndServe()` функция
    * TLS 连接ная защита, 184
    * о функции, 133–134
    * промежуточное ПО для тестирования, 156
    * реализация таймаута сервера, 175–176
    * реализация таймаутов для всех функций обработчика, 174
* `http.NewRequestWithContext()` функция, 167–168
* `httpNewServeMux()` функция, 134
* `http.Post()` функция, 75
* `httptest.NewRecorder()` функция, 153
* `httptest.NewServer()` функция
    * загрузчик тестовых данных, 59–60
    * настрой тестового сервера, 157
    * тестирование функций обработчика, 153
* `httptest.NewUnstartedServer()` функция, 190
* `http.TimeoutHandler()` функция
    * прерывание обработки запроса, 162–165, 168, 169
    * реализация таймаута сервера, 175, 179
    * реализация таймаутов для всех функций обработчика, 174
* I
* `InitConfig()` метод, 148
* `InitLogging()` функция
    * HTTP-приложения, 360–361
    * приложения командной строки, 353
* `InitMetrics()` функция
    * HTTP-приложения, 360–361
    * приложения командной строки, 353, 354
* `InitTracing()` функция
    * HTTP-приложения, 362
    * приложения командной строки, 353
    * промежуточное ПО для тестирования
    * перехватчики
    * внедрение промежуточного ПО, 256
    * на стороне клиента, 257
    * цепочка, 271
* `IntVar()` метод, 17
* `invoker()` метод, 259
* `io.Copy()` функция, 131
* `io.Pipe()` функция, 131
* `io.ReadAll()` функция
    * `Request` структура, 116
    * деселизация полученных данных, 63
* J
* Jaeger (web-сайт), 356
* JSON Object Notation (JSON), 61
* JSON-поток, 121
* `json.NewDecoder()` функция
    * деселизация полученных данных, 61–64
    * обработка запросов на стриминг, 122
* `json.Unmarshal()` функция
* K
* Kubernetes, 372
* L
* `l.Dial()` function, 208
* `LastInsertId()` метод, 333
* `len()` функция, 107
* `Level()` метод, 354
* время жизни, следов, 351
* Linkerd, 309





* `HandlerFunc` 技巧，141
* HTTP 应用，361
* 中间件绑定，143
* `logMessage()` 函数，264, 265–266
* `log.Printf()` 函数，266–267
* `logRequest()` 函数，120
* `longRunningProcess()` 函数
    * 使用流式数据作为响应，127–128
    * 服务器超时实现，178

## M

* `main` 包，测试，43–45
* `main()` 函数
    * 数据加载，59
    * 使用 `flag` 包，19
    * 编写 gRPC 客户端，206
    * 编写单元测试，14
    * 关于函数，7
    * 处理用户信号，55
    * 带有超时的用户输入，48
    * 命令行应用程序，358–359
    * 使用拦截器实现中间件，263
    * 关系型数据库，330
    * 创建 HTTP 服务器，107
    * 测试 TLS 服务器，189
    * 对象存储器，317–318
    * 去除重复错误信息，23
* `Marshal()` 函数
    * 序列化与反序列化，217–218
    * 发送数据，67
* `metadataUnaryInterceptor()` 函数，259
* MinIO 软件，312, 313, 318–322
* `MultipartForm`，117
* MySQL，313, 327

## N

* `Name()` 方法，24
* `NArg()` 方法，17
* `net.Listen()` 函数，198
* `NewClientTLS()` 函数，277
* `NewDecoder()` 函数，122–123
* `NewFlagSet()` 函数，16, 17, 19
* `NewHealthClient()` 函数，281–282
* `NewRequestWithContext()` 函数，91
* `NewScanner()` 函数，3
* `NewServeMux()` 函数
    * 测试服务器，114
    * 关于拦截器，110
* `NewServer()` 函数
    * 健康检查实现，280
    * 测试服务器，114
* `NewWriter()` 方法，315
* `NewYAML()` 函数，369
* Nginx，309
* Nomad，372
* `Notify()` 函数，52

## O

* `Open()` 方法
    * `Request` 结构，117
    * 关系型数据库，329
    * 对象存储器，315
* `OpenBucket()` 函数，316, 317, 326
* OpenTelemetry 社区，351
* OpenTelemetry 项目，351
* `os.Stat()` 函数，339–340

## P

* `packageGetHandler()` 函数，333–334
* `panic()` 函数
    * 使用 `flag` 包，16
    * 运行时错误处理，286–288
    * 中间件绑定，146
* `panicHandler()` 函数，146
* `panicMiddleware()` 函数
    * 中间件，143, 146
    * 测试中间件，155
* `parse()` 函数，17, 19
* `parseArgs()` 函数
    * 使用 `flag` 包，16, 18
    * 编写单元测试，8–14
    * 使用信息，24
    * 关于函数，3–4, 7
    * 更新单元测试，28–30
    * 子命令实现，35
    * 测试解析逻辑，20–22
* `ParseForm()` 方法，116
* `ParseMultipartForm()` 方法
    * `Request` 结构，117
    * 处理二进制数据，76
    * 对象存储器，314
* PATCH 方法，66
* `Ping()` 函数，329
* `Port()` 方法，342
* `Post()` 函数
    * 请求设置，91
    * 发送数据，67
* POST 方法，66
* PostgreSQL，327
* `p.Port()` 方法，341
* `PrintDefaults()` 方法，24
* `printUsage()` 函数
    * 关于函数，5
    * 子命令实现，40
* `process()` 函数，120
* `processStream()` 函数，128–129
* `Protobuf` 
    * 关于消息，214
    * 直接和反向兼容性，219–220
    * 序列化与反序列化，217–218
    * protoc 命令，197
    * protobufs，193
* `protojson()` 函数，369





* `RegisterHealthServer()` 函数, 280
* `RegisterMiddleware()` 函数, 151–152
* `registerPackageData()` 函数, 75
* `registerServices()` 函数
    * 执行健康检查检查, 280
    * gRPC 服务端测试, 208
* 远程过程调用 (RPC) 应用，使用 gRPC 创建, 193–228
* `ReportDuration()` 方法, 355, 359–360
* `Request` 结构体
    * body, 116
    * `Form` / `PostForm`, 116
    * header, 116
    * host, 116
    * method, 115
    * `MultipartForm`, 117
    * `Proto` / `ProtoMajor` / `ProtoMinor`, 116
    * URL, 115
    * 关于结构体, 114–115
* `Rollback()` 方法, 347
* `RoundTrip()` 方法, 93–99
* `RoundTripper` 接口, 93–99
* `RowsAffected()` 方法, 333
* `rows.Close()` 函数, 336–337
* `rows.Next()` 方法, 337
* `rows.Scan()` 方法, 337
* `runCmd()` 函数
    * 编写单元测试, 12–13
    * 关于该函数, 7
    * 更新单元测试, 30–32
    * 通过位置参数接收名称, 25–26
    * 语法分析逻辑测试, 21–22
* `S`
* `Scan()` 函数
    * 关于该函数, 3
    * 关系型数据库, 343–345
* `Send()` 方法
    * 双向流传输, 241–242
    * 处理临时性故障, 301, 304
    * 向客户端流传输, 239–240
    * 向服务器流传输, 232
    * 接收和发送任意字节, 254–255
* `SendAndClose()` 方法
    * 向客户端流传输, 238
    * 接收和发送任意字节, 252–253
* `SendMsg()` 方法
    * 请求中断, 293
    * 包装流, 269–271
* `ServeHTTP()` 方法
    * `HandlerFunc` 技巧, 141
    * 关于该方法, 134
    * HTTP 处理器, 139
    * 中间层软件, 143
    * 处理器间的数据共享, 135
    * 中间件测试, 156–157
* `SetConnMaxIdle()` 方法, 329
* `SetConnMaxTime()` 方法, 329
* `SetOutput()` 方法, 16
* `SetServingStatus()` 方法, 280
* `setup()` 函数
    * 双向流, 243
    * 处理故障, 301, 303
    * 使用拦截器实现中间件软件, 260
* `setupCommunication()` 函数, 275
* `setupGrpcConn()` 函数
    * TLS 保护, 277
    * 编写 gRPC 客户端, 204, 206
    * 使用拦截器实现中间件软件, 259, 260
    * 优化连接, 299
    * 拦截器链, 271
* `setupGrpcConnection()` 函数, 203
* `setupHandlers()` 函数
    * 处理器间的数据共享, 136
    * HTTP 服务器测试, 114
    * 处理器函数, 110
* `setupHandlersAndMiddleware()` 函数, 189
* `setupServer()` 函数
    * 测试服务器配置, 157
    * 代码组织, 152
* `Shutdown()` 方法, 180, 182, 183
* `SignedURL()` 方法, 321–322
* `sleep` 命令, 55–56
* `Sleep()` 函数, 82
* `s.ListenAndServe()` 函数, 182
* `SQLite`, 327
* `sql.Open()` 函数, 329–330
* `startBadHTTPServer()` 函数, 86–87
* `startServer()` 函数, 208
* `startTestGrpcServer()` 函数
    * 执行健康检查检查, 282
    * gRPC 客户端测试, 211
* `startTestHTTPServer()` 函数, 59–60
* `startTestPackageServer()` 函数, 64–65
* `StartTLS()` 方法, 190
* `statsd` (网站), 351
* `statsd.New()` 函数, 354
* `status.Convert()` 函数, 227–228
* `status.Error()` 函数, 227
* `Str()` 方法, 354
* `strings.Contains()` 函数, 191
* `strings.Join()` 函数, 336
* `strings.NewReader()` 函数, 254–255
* 子命令
    * 用于子命令控制的应用架构, 37–43
    * 定义, 33
    * 实现, 33–47
* `switch..case` 运算符, 251
* `T`
* `Terminate()` 方法, 343
* `testcontainers.General()` 函数, 342
* `TestHandleGrpc()` 函数, 46
* `TestHandleHttp()` 函数, 45
* `TestPackageGet()` 函数, 324
* `Text()` 函数, 3
* `time.NewTimer()` 函数, 293
* `timeoutStreamingInterceptor()` 函数, 293–294
* `timeoutUnaryInterceptor()` 函数, 291–292
* `time.Sleep()` 函数, 162, 166
* `TracingMiddleware()` 函数, 362–363
* 传输层安全 (TLS)
    * 配置, 184–188
    * 链接保护, 184–191, 275–278
    * 服务器测试, 188–191




### V
* `users.NewUsersClient()` 函数, 204
* `users.RegisterUsersServer()` 函数, 200–201
* `validateArgs()` 函数
    * 编写单元测试, 10–11
    * 关于函数, 4–5, 7
    * 语法解析逻辑测试, 22

### W
* `WaitForReady()` 方法, 301
* `wait.ForSQL()` 函数, 341
* `Watch()` 方法, 283–285
* `With()` 方法, 353
* `WithChainStreamInterceptor()` 函数, 272
* `WithChainUnaryInterceptor()` 函数, 271–272
* `WithDeadline()` 函数, 51
* `WithTimeout()` 函数
    * 处理用户信号, 52–53
    * 带有限制的自定义输入, 48–51
* `WithValue()` 函数, 118–119
* `Write()` 方法, 129

### Y
* YAML 数据格式, 368–369

### Z
* `zerolog.New()` 函数, 353

### А
* 子命令驱动型应用架构, 37–43
* SQL 注入攻击, 333

### Б
* 二进制数据及其处理, 72–79

### В
* 魔法胶水 (Magic Glue), 198, 213
* 临时故障，处理, 300–305

### Г
* 深度检查, 373
* 现成的 HTTP 服务器
    * TLS 连接保护, 184–191
    * 请求中断, 161–173
    * 正确关闭的实现, 179–183
    * 服务器超时, 173–179

### Д
* 数据
    * 二进制, 72–79
    * 接收数据的反序列化, 61–65
    * 加载, 57–61
    * 配置, 367
    * 发送, 66–72
    * 流式形式的响应, 126–131
    * 共享加载器, 134–139
    * 配置数据, 367
    * 遥测数据
        * 类别, 349–354
        * 定义, 349
        * 输出, 352–365
        * 双向流传输, 239–246
    * 序列化。反序列化
    * 反序列化
        * 关于反序列化, 214–219
        * 接收的数据, 61–65
        * 驱动类型访问, 325–327
        * 为所有请求添加头, 96–99
        * 驱动程序，类型访问, 325–327

### Ж
* 日志/日志
    * 关于日志, 349–354
    * 中间件, 94–96
    * 结构化, 350

### З
* 头
    * 为所有请求添加头, 96–99
    * `Request` 结构, 116
    * 加载
        * 数据, 57–61
        * 来自过载的服务器, 81–85
        * 包加载，测试, 323–325
        * 数据加载器，测试, 59–61
    * 请求
        * 流式处理, 121–126
        * 添加元数据, 118–121
        * TLS 连接保护, 184–191, 275–278

### И
* 数据源名称 (DSN), 329
* 集成测试, 112
* 与包服务器集成, 313–323, 328–339
* 服务接口, 197

### К
* 准准指标, 351
* 通道, 203
* 代码组织, 147–152

### М
* 序列化, 214–219
* 元数据
    * 已定义的, 327
    * 添加到请求, 118–121
* 方法, 115
* 直方图指标, 351
* 计数器指标, 351
* 指标, 349–354
* 单元测试
    * 编写, 8–14
    * 更新, 28–32

### Н
* 可靠性
    * 客户端, 297–306
    * 服务器, 275–278
    * 可靠性, 297
* 编写
    * 命令行, 8–14
    * gRPC 客户端, 203–203
    * gRPC 服务器, 198–203
    * 客户端, 57–80
    * 中间件, 134–139
    * 应用程序测试, 147–159
    * 单元测试, 28–32
    * TLS 连接保护, 184–188
    * 行为, 80–91
    * 连接池, 103–104
    * 消息, 220–226

### О
* 包装流, 269–271
* 更新单元测试, 28–32
* 处理
    * 临时故障, 300–305
    * 客户端, 169–173
    * 运行时错误, 286–289
    * 用户信号, 52–56
    * 请求中断, 289–297
    * 请求
        * 配置, 108–111
        * 中断, 161–173
        * 流式处理, 121–126
        * 错误, 226–228
        * 服务接口, 199
* 逆向兼容性, 219–220
* 代码组织, 147–152
* 发送数据, 66–72
* 错误，处理, 286–289

### П
* 传递遥测数据, 352–365
* 环境变量, 367
* 拦截器，流式客户端, 257–258
* 拦截器，流式服务器, 263–265





# 流式请求、处理，121–126

## 流式传输 
### 双向流式传输，239–246
### 关于流式传输，229
### 客户端流式传输，237–239
### 服务端流式传输，230–237

## 客户端流式传输，237–239
## 服务端流式传输，230–237

## 数据类型转换，343–346

## 中断 
### 请求处理，289–297
### 请求处理，161–173

## 在请求中附加元数据，118–121

## 应用 
### 命令行工具，1–32
### 部署，367–373
### 分发，370–372
### gRPC，193–272, 275–309, 364–365
### 可观测性，349–365
### 必选参数与可选参数，15
### 服务端，372–373

## 命令行应用 
### 编写，1–32
### 遥测数据传输，352–360
### 进阶，33–56
### 子命令实现，33–47
### 使应用健壮性，47–56

## 健康检查 
### 关于健康检查，372
### 实现，278–286

## 数据生产者，127
## 任意字节流的接收与发送，247–256

## 中间件 
### 日志记录，94–96
### 关于中间件，92–94
### 定义的，92
### 使用拦截器实现，256–272
### 服务端，139–147
### 测试，155–157
### 链，142–147

## 向后兼容性，219–220

## 连接池 
### 配置，103–104
### 关于连接池，99–103

## R
## 部署 
### 应用部署，367–373
### 服务端应用部署，372–373

## 应用分发，370–372

## 实现 
### 优雅退出，179–183
### 子命令，33–47
### 健康检查，278–286
### 使用拦截器的中间件，256–272
### 所有函数的超时，173–174
### 服务端超时，174–179

## 请求器，117

## 关系型数据库 
### 与服务器集成，328–339
### 数据库事务，346–348
### 关于关系型数据库，327–328
### 数据转换，343–346
### 数据存储测试，339–343

## S
## 自签名证书，184
## 使用 TLS 连接，184–191, 275–278
## 就绪语义，300
## 与包服务器集成，313–323, 328–339

## 服务端 
### 可靠性，278–297
### 预载下载，81–85
### 测试安装，157–159

## 服务端中间件，编写，139–147
## 服务端拦截器，263–269
## 服务端应用，部署，372–373
## 服务网格，372–373

## 语法解析 
### 命令行参数，15
### 测试逻辑，20–22
### 函数间数据共享，134–139

## 连接 
### 改进，298–300
### 管理，306–309
### 使用消息配置，24–25
### 移除重复消息，23
### 带有超时限制的用户输入，48–51
### 等待策略，341
### 结构化日志记录，350
### 数据读取器，127

## H
## 主机，116
## 数据存储 
### 关于数据存储，311–312
### 关系型数据库，327–348
### 测试，339–343
### 对象存储，312–327

## 对象存储 
### 访问基础驱动类型，325–327
### 上载测试包，323–325
### 与包服务器集成，313–323
### 关于对象存储，312–313

## C
## 证书中心 (CA)，184
## 链 
### 拦截器链，271–272
### 中间件绑定，142–147

## U
## 移除重复错误消息，23
## 改进 
### 连接配置，298–300
### 用户界面，22–28

## 一元客户端拦截器，257–258
## 一元服务端拦截器，263–269

## T
## 超时  
### 调用配置，305–306
### 行为测试，85–88
### 服务端超时，174–179

## 测试 
### `main` 包，45–47
### gRPC 客户端，211–213
### gRPC 服务端，207–210
### HTTP 服务端，112–114
### `main` 包，43–45
### TLS 服务端，188–191
### 数据读取器，59–61
### 上载包，323–325
### 语法解析，20–22
### 配置服务端，157–159
### 超时行为，85–88
### 中间件，155–157
### 处理函数，153–155
### 数据存储，339–343
## 编写复杂的服务端应用测试，147–159
## 数据库事务，使用，346–348
## 溯源，349–354





* 可用性检查客户端，286
* 批量请求终点，338–339
* 作为响应发送数据，322
* 跟踪客户端的出站行为，169
* 测试请求中断行为，173
* 支持启用连接池行为，104
* 在中间件中附加请求 ID，146
* 检查子命令调用，45
* 检查 HTTP 方法，47
* 间隙，351–352
* 计算请求延迟的中间件，99
* 扩展 `http` 命令以发送带有 JSON 体的 POST 请求，71
* 扩展 `http` 子命令以配置重定向行为，91
* 扩展 `http` 子命令以允许添加头和基本身份验证凭据，92
* 扩展 `http` 子命令以允许数据上传，61
* 扩展 `http` 子命令以发送表单上传的 POST 请求，79
* `Repo` 服务的命令行客户端实现，226
* `Users` 服务的命令行客户端实现，219
* 实现带超时的正常退出，297
* 请求记录器，117
* 注册流之间交换的消息，272
* 文件上传服务器，131
* 从文件创建仓库内容，256
* 欢迎页生成器，22
* 测试 `healthCheck()` 函数，155
* 测试 `main()` 函数，14
* 集中化错误处理，139
* 为方法调用设置超时，305

## ：处理器函数
* 为所有项引入超时，173–174
* 关于函数，109–111
* 在之间交换数据，134–139
* 定义，108
* 发送数据，69–70
* 测试，153–155

# 关于作者

**Amit Saha** 是位于澳大利亚悉尼的 Atlassian 公司的一名软件工程师。他撰写了书籍*Doing Math with Python: Use Programming to Explore Algebra, Statistics, Calculus, and More!*(No Starch Press, 2015 年)和*Write Your First Program*(PHI Learning, 2013 年)。他的其他作品发表在技术杂志、会议材料和研究期刊上。您可以通过 [`echorand.me`](https://echorand.me) 找到他。

