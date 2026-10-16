
```
assertStatus(t, response.Code, http.StatusOK)

got := getLeagueFromResponse(t, response.Body)
want := []Player{
    {"Pepper", 3},
}
assertLeague(t, got, want)
}
}
```

## 尝试运行测试

```
=== RUN   TestRecordingWinsAndRetrievingThem/get_league
--- FAIL: TestRecordingWinsAndRetrievingThem/get_league
(0.00s)
    server_integration_test.go:35: got [] want [{Pepper 3}]
```

## 编写足够代码使其通过

InMemoryPlayerStore 在调用 GetLeague() 时返回 nil，所以我们需要修复它。

```
//in_memory_player_store.go
func (i *InMemoryPlayerStore) GetLeague() []Player {
    var league []Player
    for name, wins := range i.store {
        league = append(league, Player{name, wins})
    }
    return league
}
```

我们需要做的就是遍历 map 并将每个键/值转换为一个 Player。

测试现在应该可以通过了。

## 收尾

我们继续使用 TDD 安全地迭代我们的程序，使其以可维护的方式使用路由器支持新的端点，并且现在可以为我们的消费者返回 JSON。在下一章中，我们将介绍持久化数据和对联赛进行排序。

## 我们涵盖的内容：

- **路由**。标准库为你提供了一个易于使用的类型来进行路由。它完全拥抱 `http.Handler` 接口，因为你将路由分配给 `Handler`，而路由器本身也是一个 `Handler`。然而它缺少一些你可能期望的功能，例如路径变量（例如 `/users/{id}`）。你可以轻松自行解析此信息，但如果这成为负担，你可能需要考虑查看其他路由库。大多数流行的库都坚持标准库的理念，即也实现 `http.Handler`。
- **类型嵌入**。我们稍微涉及了这种技术，但你可以从 Effective Go 中了解更多关于它的内容。如果你从中只记住一件事，那就是它可能非常有用，但 *总是。

让我们尝试将其 DRY 化为一个函数。

创建一个名为 league.go 的新文件并将此内容放入其中。

```
//league.go
func NewLeague(rdr io.Reader) ([]Player, error) {
	var league []Player
	err := json.NewDecoder(rdr).Decode(&league)
	if err != nil {
		err = fmt.Errorf("problem parsing league, %v", err)
	}
	return league, err
}
```

在我们的实现中以及 server_test.go 中的测试辅助函数 getLeagueFromResponse 中调用它

```
//file_system_store.go
func (f *FileSystemPlayerStore) GetLeague() []Player {
	var league []Player
	err := json.NewDecoder(rdr).Decode(&league)
	if err != nil {
		err = fmt.Errorf("problem parsing league, %v", err)
	}
	return league, err
}
```
