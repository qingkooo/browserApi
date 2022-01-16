# clipboard

## 已被标准废弃的接口 document.execCommand(String)

该接口的缺点：

- 内容来源必须是 UI 元素。
- 无法使用接口向剪贴板写入内容。
- 同步接口。同步相比较异步而言，如果复制/粘贴大量数据，页面会出现卡顿。
- 权限管理。不支持 permission 管理，有些浏览器会跳出提示框要求用户许可，而在用户做出选择前页面会失去响应。

为了解决这些问题，浏览器厂商提出了异步的 Clipboard API。

## data-constructure

- ClipboardEvent 继承自 Event
  - DataTransfer
- Clipboard
  - ClipboardItem

## summary

要想对系统快捷键进行监听，使用 document.addEventListener("cut/copy/paste",(clipboardEvent)=>{})

自定义写入需要自行在 promise 中监听。

## QA

- 当前缺少一个剪切板变动的事件监听。比如截屏之后，无法第一时间知晓。mdn 上关于 windiw 的 clipboardchange 事件的描述并没有作用。如何监听剪切板的变动？

- 截屏之后使用系统快捷键 cmd+paste，clipboardEvent 中的 datatransfer 中并无数据？
