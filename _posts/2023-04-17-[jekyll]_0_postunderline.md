---
layout: single
title: "[jekyll] 포스트 제목 밑줄 제거하기"
folder: "jekyll"
categories:
  - jekyll

tags: [blog, jekyll, minimal-mistakes]

author_profile: true
sidebar:
  nav: "sidebar-category"

# toc: true
# toc_label: "목록"
# toc_icon: "bars"
# toc_sticky: true
classes: wide

date: 2023-04-17
---

## 포스트 제목 밑줄 제거하기

글자 크기를 변경하고 보니 게시된 포스트들의 밑줄(underline)이 눈에 거슬린다.  
해당 밑줄을 삭제하는 방법을 찾아서 여기에 적어 둔다.

### 1. \_basis.scss 파일 수정하기 (minimal-mistakes 기준)

\_base.scss파일은 minimal-mistakes를 쓰는 사람이라면 아래와 같은 경로에 위치해 있을 것이다.

\_sass/minimal-mistakes/\_base.scss

해당파일을 열고 link가 있는 부분(126번째 줄)을 찾으면 아래와 같다.

```scss
/* links */

a {
  text-decoration: none; //이 부분만 추가해준다
  &:focus {
    @extend %tab-focus;
  }

  &:visited {
    color: $link-color-visited;
  }

  &:hover {
    color: $link-color-hover;
    outline: 0;
  }
}
```

다른 부분은 동일하고 주석으로 된 한 줄만 추가해주면 끝.  
밑줄은 사라진다.
