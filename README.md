# Base64-to-input-file

Adicionando um File ao input file HTML


Decodifica uma string base64
```
const byteString = atob(base64String.replace('data:image/jpeg;base64,', ''));
```

Converte o ArrayBuffer para String
```
const ab = new ArrayBuffer(byteString.length);
const ia = new Uint8Array(ab);
for (let i = 0; i < byteString.length; i += 1) {
ia[i] = byteString.charCodeAt(i);
}
```


Gera o File 
```
const newfile = new File([ab], "nome-do-arquivo.jpg", { type: "image/jpeg" });
```

Usado para criar uma nova FileList de maneira circular
```
 function FileListItem(a) {
a = [].slice.call(Array.isArray(a) ? a : arguments)
for (var c, b = c = a.length, d = !0; b-- && d;) d = a[b] instanceof File
if (!d) throw new TypeError("expected argument to FileList is File or array of File objects")
for (b = (new ClipboardEvent("")).clipboardData || new DataTransfer; c--;) b.items.add(a[c])
return b.files
}
```

insere o File gerado no input file 
```
const upload=document.getElementById("foto_teste");
upload.files = new FileListItem(newfile)
```


## LINKS

* [atob](https://developer.mozilla.org/en-US/docs/Web/API/WindowOrWorkerGlobalScope/atob)
* [arraybuffer](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/ArrayBuffer)
* [Uint8Array](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Uint8Array)
* [charCodeAt](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/charCodeAt)
* [File](https://developer.mozilla.org/en-US/docs/Web/API/File)
