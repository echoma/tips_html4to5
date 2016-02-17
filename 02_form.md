* 全局tabindex控制tab顺序，和autofocus属性自动获取输入焦点
```html
    <form>
      <input placeholder=tabindex是3 tabindex=3 />
      <input placeholder=tabindex是1 tabindex=1 autofocus />
      <input placeholder=tabindex是0 tabindex=0 />
      <input placeholder=tabindex是2 tabindex=2 />
      <input placeholder=tabindex是-1 tabindex=-1 />
    </form>
```
* required属性表示该属性必填

```html
    <form>
      <input placeholder=这里必填 required/>
      <input placeholder=这里选填 />
      <button>提交</button>
    </form>
```