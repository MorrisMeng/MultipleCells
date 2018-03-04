# MultipleCells
TableView of multiple types of cells . 


## 简化tableView的代理方法

* 不同类型的cell继承BaseCell实现多态赋值

* 在处理model数据的时候就把cell的cellReusedId处理好

* cell的类名作复用id

* 直接从数据源中取对应的cellReusedId，拿到对应类型的cell

```
- (UITableViewCell *)tableView:(UITableView *)tableView cellForRowAtIndexPath:(NSIndexPath *)indexPath
{
    //1、取出数据源
    Person *p = self.dataSource[indexPath.row];
    //2、根据不同的复用标识取出对应的cell
    BaseCell *cell = nil;
    cell = [tableView dequeueReusableCellWithIdentifier:p.cellReusedId];
    //3、给cell赋值
    [cell setPerson:p];
    
    return cell;
}
```
