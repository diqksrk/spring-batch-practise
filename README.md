# spring-batch-practise

## 2장 스프링 배치
1. Annotation
#### EnableBatchProcessing : 이 이노테이션은 배치 인프라스트럭쳐를 부스트스랩하는데 사용된다. 따라서, 다음과 같은 컴포넌트를 직접 포함시킬 필요는 없다.
* JobRepository : 실행중인 잡의 상태를 기록하는데 사용된다.
* JobLauncher : 잡을 구동하는데 사용된다.
* JobExplorer : JobRepository를 사용해 읽기 전용 작ㅇ버을 수행하는 데 사용됨.
* JobRepository : 특정한 런처 구현체를 사용할 때 잡을 찾는 용도로 사용됨
* PlatformTransactionManager : 잡 진행 과정에서 트랜잭션을 다루는 데 사용됨
* JobBuilderFactory : 잡을 생성하는 빌더
* StepBuilderFactory : 스텝을 생성하는 빌더
#### SpringBootApplication : @SpringBootConfiguration과 @EnableAutoConfiguration를 결합한 메타어노테이션이다.
데이터 소스뿐 아니라 스프링 부트 기반의 적절한 자동 구성을 만들어준다.
#### TaskLet 
* RepeatStatus : FINISHED - 잡을 끝내겟다.
* RepeatStatus : CONTINUABLE - 계속 실행할것을 알리는 메시지이다.

### 실행구조
* JobLauncherCommandLineRunner : 스프링 배치 클래스 경로에 있다면 실행시에 로딩.
* JobLauncher를 사용해서, Application Context에서 찾아낸 모든 잡을 실행한다.

## 4장
#### JOB의 특징
* 유일하다.
* 순서를 가진 여러 스텝의 목록이다.
* 처음부터 끝까지 실행 가능하다.
* 독립적이다 : 의존성이 없는 것은 아니지만, 자연스럽게 처리한다. 만약, 파일이 없다면 오류를 자연스럽게 처리할 것이며 파일이 전달될 때까지 기다리지 않는다.

#### JOB의 생명주기
1. JobRunner에서 처음 실행 : 잡의 이름과 여러 파마리터를 받아들여 잡을 실행시키는 역활을 한다.
* CommnadLineJobRunner : 스크립트를 이용하거나, 명령행에서 직접 잡을 실행할때 사용한다.
* JobRegistryBackgroundJobRunner : 쿼츠와 같은 스케쥴러를 통해 스케쥴링했다면, 실행 가능한 잡을 가지고 있는 JobRegistry를 생성한다.





* 부트 스트랩 : 일반적으로 한번 시작하면 알아서 진행되는 일련의 과정을 의미한다. 