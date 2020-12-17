# AJAX-1
# AJAX（上） AJAX请求css,js，html,xml,json以及实现最基础的分页
## 实现五个挑战:
### * 用AJAX加载CSS，并使其生效
```server.js 内容
//server.js
else if(path === '/style.css'){
    response.statusCode = 200
    response.setHeader('Content-Type', 'text/css;charset=utf-8')
    response.write(fs.readFileSync('public/1.css'))
    response.end()
  }
```
```main.js
//main.js 内容
getCss.onclick=()=>{
    const request= new XMLHttpRequest()
    request.open('GET','/1.css')
    request.onreadystatechange=()=>{
        if(request.readyState===4 && request.status===200){
            const style = document.createElement('style')
            style.innerHTML=request.response
            document.head.appendChild(style)
        }alert('下载失败呢')
    }
    request.send()
}
```
### * 用AJAX加载JS，并使其执行
```server.js 内容
//server.js
else if(path === '/2.js'){
    response.statusCode = 200
    response.setHeader('Content-Type', 'text/javascript;charset=utf-8')
    response.write(fs.readFileSync('public/2.js'))
    response.end()
  }
```
```main.js
//main.js 内容
getJS.onclick=()=>{
    const request= new XMLHttpRequest()
    request.open('GET','/2.css')
    request.onreadystatechange=()=>{
        if(request.readyState===4 && request.status===200){
            const script = document.createElement('script')
            script.innerHTML=request.response
            document.body.appendChild(script)
        }alert('下载失败呢')
    }
    request.send()
}
```

### * 用AJAX加载HTML，并使其出现在页面中
```server.js 内容
//server.js
else if(path === '/3.html'){
    response.statusCode = 200
    response.setHeader('Content-Type', 'text/html;charset=utf-8')
    response.write(fs.readFileSync('public/3.html'))
    response.end()
  }
```
```main.js
//main.js 内容
getJS.onclick=()=>{
    const request= new XMLHttpRequest()
    request.open('GET','/3.html')
    request.onreadystatechange=()=>{
        if(request.readyState===4 && request.status===200){
            const div = document.createElement('div')
            div.innerHTML=request.response
            document.body.appendChild(div)
        }alert('下载失败呢')
    }
    request.send()
}
```

### * 用AJAX加载XML,并获取其节点内容
```server.js 内容
//server.js
else if(path === '/4.xml'){
    response.statusCode = 200
    response.setHeader('Content-Type', 'text/xml;charset=utf-8')
    response.write(fs.readFileSync('public/4.xml'))
    response.end()
  }
```
```main.js
//main.js 内容
getXML.onclick=()=>{
    const request= new XMLHttpRequest()
    request.open('GET','/4.xml')
    request.onreadystatechange=()=>{
        if(request.readyState===4 && request.status===200){
              const dom= request.responseXML
              const text=dom.getElementsByTagName('warning')[0].textContent
              console.log(text.trim())
        }alert('下载失败呢')
    }
    request.send()
}
```

### * 用AJAX加载JSON，并将其转为对象
```server.js 内容
//server.js
else if(path === '/5.json'){
    response.statusCode = 200
    response.setHeader('Content-Type', 'text/json;charset=utf-8')
    response.write(fs.readFileSync('public/5.json'))
    response.end()
  }
```
```main.js
//main.js 内容
getJson.onclick=()=>{
    const request= new XMLHttpRequest()
    request.open('GET','/1.css')
    request.onreadystatechange=()=>{
        if(request.readyState===4 && request.status===200){
            const object = JSON.parse(request.response)
            myName.innerHTML=object.name
        }alert('下载失败呢')
    }
    request.send()
}
```

### * 可选：用AJAX模拟分页操作
