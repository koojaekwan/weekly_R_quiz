Q) 주어진 소득(= income.csv) 데이터를 이용하여 소득상위N%가 전체소득에서 차지하는 비중을 차트로 그려주세요!  
CMD(terminal : command line interface)에서 아래와 같은 Rscript 명령어로 실행할 수 있는 R 스크립트로 작성해야합니다!  

- 입력 파일 : income.csv  
- 출력 파일 : inequality_result.PNG  

> cmd call example :  
> Rscript --encoding=UTF-8 inequality_answer.R display_ratio chart_size  
> Rscript --encoding=UTF-8 inequality_answer.R ".01 .1 .3 .5" "17.8 17.8"  

display_ratio 입력값을 기준으로 차트 상의 소득상위기준% 텍스트 표시 지점을 잡아줍니다  
chart_size 입력값을 기준으로 차트의 가로, 세로 크기를 잡아줍니다

![inequality_result.PNG](inequality_result.PNG)

참고로 사용되어야 하는데 컴퓨터에 없는 package들을 repository 지정 후 install & load 하는 부분은 다음과 같습니다 :)  

```{r}
# cmd call example : 
# Rscript --encoding=UTF-8 inequality_answer.R display_ratio chart_size
# Rscript --encoding=UTF-8 inequality_answer.R ".01 .1 .3 .5" "17.8 17.8"

# needed packages
package.list <- 
  c('dplyr','ggplot2','data.table','stringr','extrafont')

# not installed packages among needed packages
not.found.packages <- 
  package.list[!package.list %in% installed.packages()[,1]]

# set repos : cran.rstudio.com
repos <- c('https://cran.rstudio.com/')
names(repos) <- 'CRAN'

# install.packages
sapply(
  not.found.packages, 
  function(x) install.packages(pkgs=x, repos=repos, type='binary', quiet=TRUE))
  
# load packages
sapply(
  package.list, 
  function(x) library(x, character.only=TRUE))
```
