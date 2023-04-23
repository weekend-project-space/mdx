# mdx

mdx = md + x

## 输入

```
let a = 'Hello mdx';
let b = [1,2,3];
------
**${a}**
${b.map(o=>'- '+o).join('\n')}

- [x] md基础语法+变量支持
- [ ] 支持import 语法
- [ ] 支持文档自动生成
```

copy 上面内容 [mdx](https://bitmagic.space/mdx/) 粘贴查看效果

## 输出

**Hello mdx**

- 1
- 2
- 3

- [x] md 基础语法+变量支持
- [ ] 支持 import 语法
- [ ] 支持文档自动生成
