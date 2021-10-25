# Spring Batch

```
# BatchApplication.java

package com.laonstory.poc_be_batch;

import org.springframework.batch.core.configuration.annotation.EnableBatchProcessing;
import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.SpringBootApplication;

@EnableBatchProcessing// 배치 기능 활성화
@SpringBootApplication
public class PocBeBatchApplication {

    public static void main(String[] args) {
        SpringApplication.run(PocBeBatchApplication.class, args);
    }

}

```
@EnableBatchProcessing : 이 어노테이션을 선언하면, Spring Batch의 여러 기능들을 사용할 수 있게 됩니다. 
선언하지 않으시면 Spring Batch 기능을 사용할 수 없기 때문에 필수로 선언하셔야만 합니다.

설정이 끝나셨으면 패키지 아래에 job 패키지를 생성하고, SimpleJobConfiguration.java 파일을 생성합니다.
___
```
#SimpleJobConfiguration

@Slf4j // log 사용을 위한 lombok 어노테이션
@RequiredArgsConstructor // 생성자 DI를 위한 lombok 어노테이션
@Configuration
public class SimpleJobConfiguration {
    private final JobBuilderFactory jobBuilderFactory; // 생성자 DI 받음
    private final StepBuilderFactory stepBuilderFactory; // 생성자 DI 받음

    @Bean
    public Job simpleJob() {
        return jobBuilderFactory.get("simpleJob")
                .start(simpleStep1())
                .build();
    }

    @Bean
    public Step simpleStep1() {
        return stepBuilderFactory.get("simpleStep1")
                .tasklet((contribution, chunkContext) -> {
                    log.info(">>>>> This is Step1");
                    return RepeatStatus.FINISHED;
                })
                .build();
    }
}
```
@Configuration
Spring Batch의 모든 Job은 @Configuration으로 등록해서 사용합니다.
jobBuilderFactory.get("simpleJob")
simpleJob 이란 이름의 Batch Job을 생성합니다.
job의 이름은 별도로 지정하지 않고, 이렇게 Builder를 통해 지정합니다.
stepBuilderFactory.get("simpleStep1")
simpleStep1 이란 이름의 Batch Step을 생성합니다.
jobBuilderFactory.get("simpleJob")와 마찬가지로 Builder를 통해 이름을 지정합니다.
.tasklet((contribution, chunkContext))
Step 안에서 수행될 기능들을 명시합니다.
Tasklet은 Step안에서 단일로 수행될 커스텀한 기능들을 선언할때 사용합니다.
여기서는 Batch가 수행되면 log.info(">>>>> This is Step1") 가 출력되도록 합니다.
___

## BATHC_JOB INSTANCE 테이블
- BATCH_JOB_INSTANCE 테이블은 Job Parameter에 따라 생성되는 테이블입니다. 
이 Job Parameter가 생소할텐데요. 
간단하게 말씀드리면, Spring Batch가 실행될때 외부에서 받을 수 있는 파라미터입니다.

- 예를 들어, 특정 날짜를 Job Parameter로 넘기면 Spring Batch에서는 해당 날짜 데이터로 조회/가공/입력 등의 작업을 할 수 있습니다.

- 같은 Batch Job 이라도 Job Parameter가 다르면 Batch_JOB_INSTANCE에는 기록되며, Job Parameter가 같다면 기록되지 않습니다.
___
# BATCH_JOB_EXECUTION 테이블
- JOB_EXECUTION와 JOB_INSTANCE는 부모-자식 관계입니다. 
JOB_EXECUTION은 자신의 부모 JOB_INSTACNE가 성공/실패했던 모든 내역을 갖고 있습니다. 

- Job Parameter requestDate=20180807로 생성된 BATCH_JOB_INSTACNE (id=4) 가 2번 실행되었고, 첫번째는 실패, 두번째는 성공했다는 것을 알 수 있습니다.

여기서 재밌는 것은 동일한 Job Parameter로 2번 실행했는데 같은 파라미터로 실행되었다는 에러가 발생하지 않았다는 점입니다. 
Spring Batch는 동일한 Job Parameter로 성공한 기록이 있을때만 재수행이 안된다는 것을 알 수 있습니다. 
___
# BATCH_JOB_EXECUTION_PARAM 테이블

- BATCH_JOB_EXECUTION 테이블이 생성될 당시에 입력 받은 Job Parameter를 담고 있습니다.
  
___
### next()
next()는 순차적으로 Step들 연결시킬때 사용됩니다. 
step1 -> step2 -> stpe3 순으로 하나씩 실행시킬때 next() 는 좋은 방법입니다.

