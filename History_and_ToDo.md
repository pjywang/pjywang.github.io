## Changed default home page
충돌 방지를 위해 index.html을 삭제 -> home.md가 메인 페이지로 설정됨. 메인 페이지로 설정되는 원리는 permalink: / 로 표현되어 있기 때문. permalink: /about 인 경우, 블로그주소/about을 했을때 해당 md (or html) 파일을 로드하게 된다.

기존 home layout이 posts의 list를 기본으로 출력하도록 되어있어서 곤란했다. 다행히, [minimal-mistakes document](https://mmistakes.github.io/minimal-mistakes/docs/layouts/)에서 single layout이 제일 기본적인 two-column form이라고 설명해주어 그것으로 바꿈.

### Deleted header link in single layout
home.md의 첫 선언에서 title로 설정된 텍스트를 hyperlink로 header에 생성하는게 디폴트인 상태였고, 보기에 안이뻐서 곤란했다. 

이를 삭제하기 위해 _layouts/single.html 에서 해당 링크를 생성하는 header 파트를 발견, 전원 주석처리하여 문제 해결.

## CV.pdf directory
docs 폴더에 저장했을때 인식 안됨: _config.yml에서 경로 무시 설정이 되어있었다.
그냥 assets 폴더에 넣어둠


# Text size modification via _sass..
Need more study!

진짜 어떻게 해야 하지ㅜㅜ _reset은 그렇게 마음에 들진 않는데

## Automatic margin produced by headers h2~h6
헤더 h1이 글자가 너무 커서 h2로 했더니 윗줄이 하나가 추가되는 곤란한 문제 발생했음.  
``_sass/base.scss`` 파일에서 h2의 margin-top을 0.2em으로 설정하였음!



# To Do
3. Email address를 아이콘 말고 그냥 글로 보여주도록
2. 본문 글자크기만 따로 조정이 가능하도록 _sass 공부하기
1. md에서 3. 2. 1 순으로 enumerate을 해도 3. 4. 5. 식으로 넘버가 붙는다.
0. 링크를 파란색 말고 조금 더 theme에 어울리는 색을 찾아봐도 좋을 것 같다. 갈색이나 보라색?