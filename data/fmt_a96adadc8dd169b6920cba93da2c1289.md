
```ts
const { api } = ccApi;

return new Promise((resolve, reject): void) => {

  const unsubscribe = api.tx.creditcoin

    .addAskOrder(

      lenderRegAddr.itemId,

      createCreditcoinLoanTerms(api, loans),

      expirationBlock,

      askGuid.toString(),

    )

    .signAndSend(lender, { nonce: -1 }, async ({

      dispatchError, events, status

    }) => {

      await extractFee(resolve, reject, unsubscribe,

        api, dispatchError, events, status);

    })

    .catch((error) => reject(error));

}).then((fee) => {

  expect(fee).toBeGreaterThanOrEqualTo((global as any).

    CREDITCOIN_MINIMUM_TXN_FEE);

});
```

此集成测试套件的核心重点是执行每个可外部调用（extrinsic），以确保可以从外部访问。在实际检查方面，主要重点是断言交易费用不会低于 `0.01 CTC`。实际上，此值可以通过参数进行配置，并允许误差范围，因为费用不是固定的，还取决于区块链的使用程度。

此集成测试套件还测试了自定义 RPC、自定义指标、一些明显的错误情况以及完整的生命周期，并将测试结果以良好的人类可读格式呈现。

```
PASS src/test/collect-coins.test.ts (49.97 s)
CollectCoins 请求
+ - 费用至少为 0.01 CTC (10 ms)
- 000 - 使用混合以太坊地址应抛出 IncorrectSender (11797 ms)
- 001 端到端 (15014 ms)
- 未找到 txHash 时应抛出 TransactionNotFound (9984 ms)
fail
- - 费用至少为 0.01 CTC (8 ms)
- 费用至少为 0.01 CTC 但被 OCW 跳过 (8 ms)

PASS src/test/register-funding-transfer.test.ts (59.98 s)
RegisterFundingTransfer
+ - 费用至少为 0.01 CTC (29060 ms)
- 如果传输无效则发布失败事件 (29987 ms)

PASS src/test/close-deal-order.test.ts (70.005 s)
CloseDealOrder
+ - 费用至少为 0.01 CTC (69127 ms)
```

这些许多集成测试由配置变量控制，Jest 使用配置文件，有时甚至会被跳过，因为我们添加了在多个环境（甚至是生产环境）中执行它们的机会。在主网中，这作为一种健全性测试，确保贷款周期功能仍然正常，并且交易费用符合最低要求。

## 健全性测试与静态分析

在此类别中，我将大部分不属于其他类型的内容分类：linter（代码检查）、代码格式化程序和自定义脚本——我喜欢遵循语言设定的最佳实践并编写整洁的代码。用于测试 Creditcoin 的工具包括 `cargo fmt`、`Clippy`、`eslint` 和 `prettier`。

在某些情况下，静态分析工具可以检测出可能导致 bug 的模式，我确保创建定制化工具来检查源码中的此类模式。在某些语言生态系统中，这种努力以 linter 插件的形式存在，而在 Creditcoin 的情况下，这些大多是独立的 bash 脚本。这些脚本将检查源代码（例如使用 `grep`），并向我们警告可能导致错误的常见错误。例如：

- 记住存在原生运行时和链上运行时，使用哪一个取决于运行时版本号？现在想象一下运行时行为改变但版本号没有改变的情况——这可能导致节点运行不同版本的代码。在许多情况下需要增加版本号，因此此脚本采取了预防性方法，并根据简化的启发算法要求增加版本号。有时这种版本号的增加并非绝对必要，但防患于未然。它也与开发过程的其他部分完美契合。

- Extrinsic 函数在其 pallet 源码中的定义顺序直接转换为它们在链元数据中的内部索引。这些索引直接转换为用户可见的错误信息（由 `polkadot-js` API 库解析），因此，我们需要确保 extrinsic 的顺序没有发生变化。该 bash 脚本是 `polkadot-js-metadata-cmp` 工具的封装。

- 为了确保交易费用准确，每个 extrinsic 都有一个关联的权重，该权重由关联的基准函数生成。确保所有内部定义的 pallet 都有基准测试，并将这些基准测试挂接到 CI 中以自动生成权重。此外，确保 extrinsic 名称、基准函数和权重函数匹配，以尽可能避免复制粘贴错误。

- 我们希望保持依赖项更新并使用各种安全相关的工具，这些工具通常通过扫描包版本并与流行的第三方包仓库进行匹配来运行。因此，不推荐使用 git 仓库中的库。对于 Rust，优先使用 package crates。

- 某些静态分析工具是为了提高质量。在健全性范畴内，我们正在构建集群并确保它不会崩溃，容器暴露 `/health` 端点供 DevOps 使用——确保代码看起来很漂亮。

## 机器人测试

在 Creditcoin 2.0 的开发过程中发生了许多自动化操作。我将它们称为“机器人测试”，但严格来说它们大多数与开发过程有关。无论如何，将其自动化都有其优势：

- 机械任务减少了人工干预。
- 它们会定期进行。
- 会自动打开拉取请求，从而触发 CI/CD 流水。

## Dependabot

第三方依赖的自动更新是 Creditcoin 2.0 的组成部分，也是我个人多年使用的功能。该服务按计划运行，并在依赖项有新版本时打开拉取请求。大多数请求与 `creditcoin-js` 和集成测试有关，因为它们是用 TypeScript 编写且更新频繁。然而，即使在 Rust 侧，我们也希望尽可能更新。这从长远来看减少了维护负担，让你知道测试软件是否与新库兼容，并对提高整体安全性做出微贡献。如果 CI 工作通过，则合并更新的版本，通常由 QA 工程师进行评审。

一个例外是 Substrate 框架本身，它是通过 git 仓库使用的。Substrate 的各种组件很少通过 `crates.io`（Rust 包仓库）发布，并且需要手动更新。该过程在 Creditcoin 2.0 中尚未实现自动化。从技术上说，很容易创建自己的机器人来为 Substrate 框架的新版本提出更新，即使是通过 git fork 使用的。我的印象是 Substrate 仍在频繁变化，需要手动工作来检查和评估任何不兼容性，因此自动化此过程可能没有太大收益。

## 使用 Gluwa-bot 进行类型定义

任何基于 Substrate 的链都会以 SCALE 格式（二进制编码）序列化数据类型和错误消息，并通过 RPC 暴露这些元数据。使用 Polkadot JS 库构建的客户端可以使用此刷新它们内部的 TypeScript 定义，并始终与区块链节点的实现保持同步。这使得 JavaScript 组件的类型检查运行得良好，反过来将某些错误的检测转移到了静态分析层面。强类型让测试人员的工作变得更加轻松！

Creditcoin 2.0 在 CI 中运行测试时会自动刷新类型定义，并自动提交和推送这些更改到 pull request 的当前分支。为了避免 CI 无限循环，大多数 GitHub 任务不会在自动化提交时重复执行。需要说明的是——在 CI 中执行任何测试之前，所有类型都已更新，并且只有在这些测试通过时，更改才会包含在提交中。

## 使用 Gluwa-bot 进行基准测试和权重生成

在 Substrate 中，基准测试（benchmark）是一种发现链上操作（extrinsic）计算复杂性的程序方法。通常情况下，它与存储读写次数有关。基准文件由人工编写。

然后，基准测试作为 CI 的一部分被执行，以确保它们可以编译且不会崩溃。这是健康测试部分。

在发布之前，会在参考硬件上执行基准测试，生成的权重会被提交到发布分支。因为这与开发分支不同，同一个提交也会自动重新变基（rebase）并针对开发分支发布一个 pull request。这确保了所有内容都得到了发布，同时也通过开发分支，最大限度地减少未来的偏差以及在 git 中解决冲突的需求，特别是在发布过程中。

## 迁移与升级测试

在内部调包（pallets）中，只有 `pallet/creditcoin/` 包含了存储迁移。它们按顺序命名为 v1、v2、v3 等，每一个都在模拟环境中通过单元测试进行验证。

这是为了确保迁移函数按预期运行——换句话说，存储项实际上被迁移（类似于 ORM 应用中的数据库迁移）。该模拟环境还测试了迁移前后的钩子（hooks），作为对迁移函数内部错误的早期警示。然而仍然存在一些不确定性：

- 我们遗漏了边缘情况
- 迁移在实际生产数据上是否可行

这些不确定性通过两个额外的测试任务来：

1. 模拟升级过程并确保其不会崩溃
2. 模拟链上状态和本地存储，确保存储迁移能够应用而不会崩溃

相同的模拟通过两种不同的方法执行：

1. 通过 `try-runtime`：这是 Substrate 框架提供的一功能集，允许在内存中模拟升级和迁移。它查询生产 RPC 端点以获取当前链上状态并在本地内存中进行复制。然后它针对本地内存存储执行迁移。如果没有失败，我们就认为成功。这可以被视为运行时升级的健康测试。详细的上游文档见 https://paritytech.github.io/try-runtime-cli/try_runtime/
2. 分叉链并升级：这种方法更接近现实，因为它消耗真实的生产数据并执行真实的运行时升级（在隔离环境中）。

首先，我们启动一个 `creditcoin-node` 并与已有的区块链同步——例如测试网或主网，取决于我们的发布目标。然后使用一个名为 `creditcoin-fork` 的辅助工具 https://github.com/gluwa/creditcoin-fork，抓取当前的链上状态并记录到 JSON 文件中。该 json 文件代表了一个新的链规范，其中创世区块是最新链上状态的副本。这允许我们执行一个本地链，其存储项与生产版本匹配，但仍向其中注入开发账户并独立运行。当新创建的本地链运行时，执行运行时升级以触发存储迁移。通过后，针对分叉执行集成测试套件，以确保分叉在功能上与原始一致。

对于升级和迁移测试，我们使用自托管的 GitHub runners，这些 runners 按需在 Azure 中部署。这是因为升级和迁移工作流需要大量内存——至少 16 GB。区块导入过程也是计算密集型的。

为了方便这些测试活动，通过两种方式对存储迁移钩子进行了实例化：

- 每次迁移都有一个迁移前后钩子，允许我们在进行断言（assertions）时共享迁移前后的状态。由于存储迁移是在运行时执行的，我们利用了 Rust 中的 `assert!` 宏会导致运行时恐慌（panic），即如果断言失败，它将导致进程崩溃。非零退出码会导致 CI 任务报告失败。

- 在可能存在边缘情况的语句周围使用 `warn_or_panic!` 宏。在生产节点中，此宏只会产生警告；但在测试期间，它也会导致崩溃。这种行为通过测试期间显式配置的编译器标志进行控制。你可以认为这是最后一道防线，你希望在测试期间通过崩溃来提醒你生产数据中已存在的边缘情况，但你不希望它在生产环境中崩溃或意外导致区块链宕机。该宏的作用正如其名——要么记录警告，要么导致恐慌。
- 一个辅助静态分析脚本，当迁移源直接使用 `log::warn!` 宏时，该脚本会失败。这有助于确保我们始终使用 `warn_or_panic!` 宏，并且不会无意删除或绕过它。否则，由实际生产数据触发的边缘情况分支在测试期间不会失败，团队可能无法意识到这一点。

除了所有这些之外，`creditcoin` pallet 定义了一个 `STORAGE_VERSION` 常量，它必须与最后一次迁移的编号匹配。这在每次迁移以及静态分析脚本中都被强制执行——最后一个迁移文件的编号必须与 pallet 中定义的 `STORAGE_VERSION` 值匹配。以下是迁移如何在两个 pallet 之间移动存储项的示例：

```rust
impl<T: Migrate> Migration<T> {

    fn pre_upgrade(&self) -> Vec<u8> {

        let count: u32 = Authorities::<T>::iter().count();

        assert!(count != 0, "Authorities not found during migration");

        let old_pallet = TaskScheduler::<T>::name();

        let new_pallet = SCHEDULER_PREFIX;

        if old_pallet == new_pallet {

            log::info!(

                target:"runtime::creditcoin",

                "pre-migrate V7, nothing to do.",

            );

            return vec![];

        }

        let storage_prefix = Authorities::<T>::storage_prefix();

        let new_pallet_prefix = twox_128(new_pallet.as_bytes());

        let authorities_prefix = [&new_pallet_prefix, &twox_128(storage_prefix)].concat();

        let new_pallet_prefix_iter = frame_support::storage::KeyPrefixIterator::new(

            authorities_prefix.clone(),

            authorities_prefix,

            |key| Ok(key.to_vec()),

        );

        assert!(new_pallet_prefix_iter.count() == 0,

            "Expected new authorities storage to be empty"

        );

        assert!((crate::Pallet<T> as GetStorageVersion)::on_chain_storage_version() < 8);

        count.to_le_bytes().to_vec()

    }

    fn migrate(&self) -> Weight {

        let count: u32 = Authorities::<T>::iter().count();

        saturated_into();

        let creditcoin = TaskScheduler::<T>::name();

        move_storage_from_pallet(

            Authorities::<T>::storage_prefix(),

            creditcoin.as_bytes(),

            SCHEDULER_PREFIX.as_bytes(),

        );

        crate::weights::WeightInfo::<T>::migration_v7(count)

    }

    fn post_upgrade(&self, ctx: Vec<u8>) {

        assert_eq!(

            StorageVersion::get::<crate::Pallet<T>>(),

            7,

            "expected storage version to be 7 after migrations

            complete"

        );

        let new_pallet = SCHEDULER_PREFIX;

        let new_pallet_prefix = twox_128(new_pallet.as_bytes());

        let past_count = useize::from_le_bytes(ctx.try_into().unwrap());

    }

}
```

```rust
assert_eq!(new_pallet_prefix_iter.count(), past_count);
```
