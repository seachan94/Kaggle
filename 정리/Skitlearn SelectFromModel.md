

# Feature Engineering & Feature Selection & Feature Extraction 
    
      Feature Engineering : 도메인 지식을 사용하여 데이터에서 피처를 변형 / 생성하는 것
      Feature Extraction : PCA 등을 통해 새로운 중요 Feature를 추출하는 것
      Feature Selection  : 기존 피처에서 원하는 피처만 변경하지 않고 선택하는 과정
      
    
## 장점

      1. 모델의 단순해지기 때문에 사용자가 더 해석하기 쉬어짐
      2. Training Time 이 절감됨
      3. Overfitting을 줄임으로써 Generalization 가능
      4. 차원이 매우 높아 발생하는 차원의 저주 방지 가능
      
      
      
# Why Feature Selection

    Feature Selection을 진행하기 앞서
    왜 우리는 모든 Feature를 ML Algorithm에 주어 어떤 Feature가 중요한지를 결정하게 하면 안될까?
    
    
    1. 차원의 저주
        
       데이터를 열의 수보다 많이 제공 할 수 있으면 Training data에 대해 완벽한 모델을 내놓겠지만
       우리는 새로운 데이터에 대해 잘 적응 할 수 있는지에 대한 (generalization) 고민을 해보아야 한다.
       
    2. Occam's Razor 법칙
    
        많은 방법 중 가장 설명하기 쉬운 방법을 선택해야 한다는 이론
        ( Feature가 많아지면 설명하기 어려워 진다.)
        
    3. Garbage In Garbage out
    
        만일 제공하는 정보가 Ex) 이름 / ID 같은 변수이면 큰 정보를 제공하지 못한다.
        
        
        
    또한 많은 기능으로 인해 모델이 커지며 시간이 오래 걸리고 생산 구현이 어려워진다.
    
    
    
    
# Feature Selection을 위한 3가지 방법


  ## Filter Method
     
      통계적 측정 방법을 사용하여 Feature들의 상관 관련성을 찾는 방법이다.
      하지만 Feature간의 상관계수가 반드시 모델에 적합한 Feature라고 할 수 없으며 Set의 조정이 정확하지 않다.
      대신 계산속도가 빠르고 상관관계를 알아내는데 적합하기 때문에 Wrapper method를 사용하기 전에 전처리로 사용한다.
      
      
       1. Information Gain
       2. Chi - square test
       3. fisher score
       4. correlation coefficient
       5. variance threshold
       
       
  ## Wrapper method
  
      예측 모델을 사용해 Feature Subset을 계속 테스트하는 방법
      기존 데이터에서 테스트를 진행 할 hold-out set을 따로 두어야 한다.
      이렇게 subset을 체크하면 어떤 Feature가 필요한지 알 수 있지만 Computing Power가 굉장히 크기 때문에
      random hill-climbing과 같은 휴리스틱 방법론을 사용
      
      
       
    
 ### 1. Recursive Feature Elimination( RFE )
          
          SVM을 사용하여 재귀적으로 제거하는 방법
          
### 2. Sequential Feature Selection (SFS)         
       
          그리디 알고리즘으로 빈 subset에서 Feature를 하나씩 추가하는 방법
          
          
 ### 3. genetic algorithm
### 4. Univariate selection
### 5. Exhaustive
### 6. mRMR
      
     Feature의 중복성을 최소화 하여 Relevancy를 최대화 하는 방법
     
      
 ## Embedded Method 
 
    모델에 정확도에 기여하는 Feature를 학습한다.
    좀 더 적은 계수를 가지는 회귀식을 찾는 방향으로 제약조건을 주어 제어하는 방법이다.
    
    
    LASSO : L1-norm을 통해 제약 주는 방법
    Ridge : L2-norm을 통해 제약을 주는 방법
    Elastic Net : 위 둘을 선형결합한 방법
    SelectFromModel
    decision tree 기반 알고리즘에서 피처를 뽑아오는 방법입니다. (RandomForest나 LightGBM 등)
    
