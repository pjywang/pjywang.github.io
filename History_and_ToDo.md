23.09.05 history: main page modified & linkedin link deleted

다음 블로그 포스팅으로 MM theme의 구조를 어느 정도 파악 가능하다: https://ansohxxn.github.io/blog/jekyll-directory-structure/

## Changed default home page
충돌 방지를 위해 index.html을 삭제 -> home.md가 메인 페이지로 설정됨. 메인 페이지로 설정되는 원리는 permalink: / 로 표현되어 있기 때문. permalink: /about 인 경우, 블로그주소/about을 했을때 해당 md (or html) 파일을 로드하게 된다.

기존 ``home`` layout이 posts의 list를 기본으로 출력하도록 되어있어서 곤란. 다행히, [minimal-mistakes document](https://mmistakes.github.io/minimal-mistakes/docs/layouts/)에서 ``single`` layout이 제일 기본적인 two-column form이라고 설명해주어 그것으로 바꿈.

### Deleted header link in single layout
home.md의 첫 선언에서 title로 설정된 텍스트를 hyperlink로 header에 생성하는게 디폴트인 상태였고, 보기에 안이뻐서 곤란했다. 

이를 삭제하기 위해 _layouts/single.html 에서 해당 링크를 생성하는 header 파트를 발견, 전원 주석처리하여 문제 해결.


# Adjustment of _config.yml
## Displaying email address directly
``links`` 파트에서 ``label``: "pjywang2@gmail.com" 로 레이블 설정하면 끝.

## CV.pdf directory
docs 폴더에 저장했을때 인식 안됨: ``_config.yml``에서 경로 무시 설정이 되어있었다.
그냥 assets 폴더에 넣어둠


# Various modifications via _sass..
``_reset.scss`` 에서 텍스트 사이즈 줄이는건 완전히 폐기한다. 항목별 customizing이 불가능하다.

다음의 awesome guide site https://www.cross-validated.com/Personal-website-with-Minimal-Mistakes-Jekyll-Theme-HOWTO-Part-II/ 를 이용한다.

scss 기본 문법은 html 혹은 md 파일들의 스타일을 다 조정할 수 있다. 다만 html 용어를 잘 이해해야 이해가 가능하다.
- \<p> : Paragraph
- \<dl> : Description list
- \<li> : List item
- \<h1> to \<h6> : HTML headings

``_page.scss`` 에서 ``.page__contents``를 찾아서 들어간 다음, 이들 각각의 font size를 조정할 수 있다!!!  
예를 들어 p, li, dl에 정의된 font-size는 default가 1em으로 설정되어 있었는데, 이를 0.8~0.9em으로 조정한다.

### scss 파일들의 동작 원리를 이제 좀 알 것 같다!!!
온갖 알 수 없던 용어들이 사실은 위 처럼 html 속성들에 대한 스타일 설정을 하는 원리였다. 링크에 대해서 수정을 하고 싶다면 \<a>에 해당하는 a 글자 하나만 찾아서 설정을 바꾼다.

``_base.scss``에 들어가면 제일 기본 베이스로 깔고 가는 레이아웃이 나온다. 여기서 margin 등이 설정 되어 있는 것을 관찰할 수 있고, 내가 조정이 가능하겠구나 하는 깨달음도 얻는다.

#### Automatic margin produced by headers h2~h6
헤더 h1이 글자가 너무 커서 h2로 했더니 윗줄이 하나가 추가되는 곤란한 문제 발생했음.  
``_base.scss`` 파일에서 h2의 ``margin-top``을 0.2em으로 설정하였음!

#### Page에서 마음에 안드는 header 아래의 boarderline 제거
page 속성에서만 제거하길 원하였고, 따라서 ``_page.scss`` 통하여 border-bottom 관련 속성을 주석 처리.

#### 하이퍼링크들의 색상 및 옵션 변경하기
이는 skin theme에 depending하는 옵션이므로, ``skin`` folder의 ``_contrast.scss`` 에서 설정한다 (내가 contrast theme을 사용 중이므로 contrast에 들어가는 것; 다른 theme 사용 시 해당 이름으로 가기).

``_base.scss``의 links 속성, 즉 a에 해당하는 칸에서 에서 밑줄 자체를 제거할 수는 있는데, 밑줄이 있으면서 보기 좋은 색상인게 더 나은것 같아서 해당 코드는 삽입했다가 주석처리하여 폐기하였음.

* 사이트 좌 상단의 블로그 bold title은 _config.yml 에서 masthead_title을 수정!

##### 헤더 쪽 링크의 animation 시뻘건 밑줄 색 수정 (절반 완료)
헤더 쪽의 링크는 cursor 접근 시 밑줄 색이 너무 시뻘건 색(``contrast`` theme에 기본으로 설정된 ``primary_color``)이라 보기 좋지 않음.  
``_masthead.scss``에서 수정 여지를 찾아본다. 이게 제일 위쪽 돛대 꼭대기를 뜻하는 단어! 마스트의 머리!  
개발자 도구 상으로는 ``_masthead``가 맞는 것 같은데, primary color를 쓴다고 사용하는 animation을 찾지 못했다.
``_animation.scss`` 에서도 찾지 못함..

차선책으로 그냥 contrast theme의 default color 에서 primary를 회색으로 바꿔버렸다 그냥


#### Width 조정하기
``_variables.scss``의 최하단에서 이를 조정하였음.  
사실 _variables에는 scss에서 자주 사용하는 '변수 이름'들이 저장되어 있다. 이들이 선언되어 있는 곳.  
Color의 이름, width의 이름 등을 적으면 어떤 색과 width, fontsize 등이 사용될지를 미리 선언해둔 곳이다.  
여기서 뭘 조정하는게 옳지는 않다.

다만, 모르는 color, width, fontsize 등이 코드에 등장할땐 항상 ``_variables.scss``에서 **정의를 찾아볼 수 있다**!!!

##### 차라리 sidebar 자체를 조정하는게 나을 수도 있다.
``_sidebar.scss`` 고고  
여기서 내 사진 동그라미를 rectangle로 바꾸었다!! ``img`` 항목을 찾은 후에, ``max-width`` 설정으로 크기를 바꾸었고, ``border-radius``를 0%로 만들어서 원형의 그림이 나오지 않도록 함. 사진 아래에 margin도 ``margin: auto;``로 추가하였다.

margin도 조금 조정해서 더 보기 좋게 만듦. ``.author__content``의 width도 100% 에서 80%로 줄여 더 보기 좋게 만들었다.  
막 적는 것들 말고도 Katerina Bosko의 github 사이트 참고하여 엄청 바꿨다!! 여기 ``_sidebar.scss``는 엄청 참고함+_+

#### 사진 불투명해지는 것 없애기
``_sidebar.scss``에서 조정할 수 있다. 거의 제일 처음 부분에 ``opacity`` 라는 요소의 설정이 있는데, 이게 hover를 하지 않으면 0.75로 설정되어 있다가, hover 시에 1로 바뀌도록 되어 있다 (즉 커서 없을때 fadeout 되는 맘에 안드는 부분!). 그냥 전부 1로 설정해버려 fadeout option을 삭제했다.


# To Do
* masthead의 아이콘들 밑줄 색깔 바꿔야 한다 (굉장히 차선책으로 일단 해결.. masthead가 아닐 수도 있으며, 어떻게든 위쪽 navigation 링크들의 색상 bold 등을 바꿔보고 싶다. attribute을 찾아야 함!)
* 제일 아래쪽에 까만 줄을 없앨지 말지 고민을 좀 해보자.
* 블로그 포스팅 각을 재야 한다.
    - 이거 posts에 md file들이 충분히 많지 않으면 뭔가 jekyll build가 안되는데 이유를 모르겠다.
    - Sample posts를 그냥 아무데나 모아놓고, 내가 원하는 포스트들로 채우고 싶은데, 일단은 좀 곤란하다 ;ㅁ;


# Contents
* Home 화면은 CV와 congruent하게 맞춘다.
* Github repository가 있는 works는 publication 옆에 link를 같이 달아준다.
* 