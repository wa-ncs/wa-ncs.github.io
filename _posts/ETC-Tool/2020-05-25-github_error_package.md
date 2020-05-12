---
layout: post
title: MarkDown_tutorial
comments: true
categories: [ETC/Tool]
tags: [Tool]
author: soobinnn
userImage: /assets/user-img/bspark.jpg
---

# MarkDown

1. 제목 표시
2. Editor
3. Registe My Image
4. Write Post
5. Upload Posts
6. Update Check

<br/>

### 1. Git Clone 

|  <center>마크다운</center> |  <center>실행결과</center> |
|:--------|:--------:|
| ``` ``` | ``` a=1 ``` |
|         |             |
|         |             |
|         |             |
|         |             |

```
# h1
## h2
### h3
#### h4
##### h5
```

<br/>

### 2. Execute Editor

에디터 실행하여 받은 Clone 프로젝트를 엽니다.

> 본 포스팅은 `VS Code` 에디터를 사용했습니다. 원하시는 에디터를 사용하시면됩니다.

<br/>

### 3. Registe My Image

자신의 사용할이미지파일을 __`assets/user-img/`__ 하위에 __`깃아이디명.png/jpg`__ 으로 저장합니다.

![blog-info-1](/assets/post-img/tool/blog-info-1.PNG)

<br/>

### 4. Write Post

__`_posts/`__ 하위에 내가 작성해야할 폴더 아래에 __`.md`__ 파일을 생성합니다.

> \* 카테고리 등록은 나중에 설명 추가 할 예정

본 예시는 회의록 작성 기준으로 설명하겠습니다.

__`_posts/Project-Minutes`__ 디렉토리 하위에 ex) __`2020-05-09-3-minutes.md`__ 파일을 생성합니다.

파일 상단에는 아래정보를 입력합니다.
```
---
layout: post
title: 2020/05/03 회의록
comments: true
categories: [Project/Minutes]
tags: [Minutes]
author: soobinnn
userImage: /assets/user-img/imsoobin.png
---
```

회의록의 경우 title, author, userImages를 변경합니다.

그아래에 글을 작성하면됩니다.

<br/>

#### 해당 포스트에 이미지를 추가하고싶을 경우

__`assets/post-img/카테고리명/`__ 하위에 __`해당게시글-순번.png/jpg`__ 로 사진을 저장합니다.

ex) 2020-05-09-blog-info.md 파일에 사진을 올리고 싶을 경우

__`assets/post-img/tool/blog-info-1.png`__ 로 저장 합니다.

![blog-info-2](/assets/post-img/tool/blog-info-2.PNG)

그 후에 해당 글에서 마크다운 형식으로 이미지를 불러옵니다.
```
// 마크다운 이미지 올리는 규칙
// ![이미지 명칭](이미지 경로)

![blog-info-1](/assets/post-img/tool/blog-info-1.PNG)
```
해당 경로와 명을 입력하면

이미지가 올라갑니다.

<br/>

### 5. Upload Posts

글을 다 작성하고 난 후 글을 올리시려면 Git push하시면됩니다.

```
git pull

git add .

git status

git commit -m "회의록 추가"

git push origin
```

<br/>

### 6. Update Check

[wa-ncs.github.io](https://wa-ncs.github.io/) 에 들어가서 글이 올라갔는지 확인하시거나,

Slack __`Blog`__ 채널에서 올라간 것을 확인할 수 있습니다.

![blog-info-3](/assets/post-img/tool/blog-info-3.PNG)

