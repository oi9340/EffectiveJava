<h2>스프링부트 시작하기<h2>
<h3>1. 프로젝트 생성</h3>
<h3>2. build.gradle 수정</h3>
<h6>2.1 프로젝트 플러그인 의존성 관리를 위한 설정</h6> 
- spring-boot-gradle-plugin라는 스프링부트 그레이들 플러그인의 2.1.7.RELEASE를 의존성으로 받도록 설정 
- ext
    - 전역변수 설정
<pre>
buildscript {
    ext{
        springBootVersion = '2.1.7.RELEASE'
    }
    repositories {
        mavenCentral()
        jcenter()
    }
    dependencies {
        classpath("org.springframework.boot:spring-boot-gradle-plugin:${springBootVersion}")
    }
}
</pre>
<h6>2.2 필수 플러그인 추가</h6>
- io.spring.dependency-management 플러그인은 스프링 부트의 의존성들을 관리해주는 플러그인이라 꼭 추가해야 함
<pre>
apply plugin: 'java'
apply plugin: 'eclipse'
apply plugin: 'org.springframework.boot'
apply plugin: 'io.spring.dependency-management'
</pre>
<h6>2.3 repositories 선언</h6>
- repositories는 각종 의존성(라이브러리)들을 어떤 원격 저장소에 받을지를 정함
- mavenCentral 기존에 많이 사용하는 저장소이지만 본인이 만든 라이브러리를 업로드하기 까다로움
- 최근에 나온 jcenter는 라이브러리 업로드도 간편하며 mavenCentral에도 업로드 될 수 있도록 자동화가 가능
<pre>
repositories{
  mavenCentral()
  jcenter()
}
</pre>
<h6>dependencies 선언</h6>
- 프로젝트 개발에 필요한 의존성들을 선언하는 곳
- 특정버전을 명시하지 않아야 org.springframework.boot:spring-boot-gradle-plugin:${springBootVersion}의 버전을 따라감
<pre>
dependencies{
    compile('org.springframework.boot:spring-boot-starter-web')
    testCompile('org.springframework.boot:spring-boot-starter-test')
}
</pre>
