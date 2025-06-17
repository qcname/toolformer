

::: {.cell 0=‘h’ 1=‘i’ 2=‘d’ 3=‘e’}

``` python
from nbdev.showdoc import *
```

:::

::: {.cell 0=‘e’ 1=‘x’ 2=‘p’ 3=‘o’ 4=‘r’ 5=‘t’}

``` python
from abc import abstractmethod
import wolframalpha
from langchain import PromptTemplate
class BaseApI:
    def __init__(self,
                 name: str, # the name of API CALL
                 prompt_template:PromptTemplate,
                 sampling_threshold: float=0.2,
                 filtering_threshold: float=0.2):
        self.name=name 
        self.prompt_template=prompt_template 
        self.sampling_threshold=sampling_threshold 
        self.filtering_threshold=filtering_threshold 

    @abstractmethod
    def execute(self):
        pass
    def __call__(self,*args:str,**kargs:str) -> str:
        output=self.execute(*args,**kargs)
        return str(output)
```

:::

::: {.cell 0=‘e’ 1=‘x’ 2=‘p’ 3=‘o’ 4=‘r’ 5=‘t’}

``` python
class CalcuatorAPI(BaseApI):
    def execute(self,input:str)->str:
        try:
            return eval(input)
        except:
            return ""
```

:::

::: {.cell 0=‘e’ 1=‘x’ 2=‘p’ 3=‘o’ 4=‘r’ 5=‘t’}

``` python
class WolframeAPI(BaseApI):
    def __init__(self,*args,api_key:str,**kargs):
        super().__init__(*args,**kargs)
        #self.api_key=api_key
        self.api_key="4QR5HP-A8KLX2RG35"
    def execute(self,input:str)->str:
        client=wolframalpha.Client(self.api_key)
        res=client.query(input=input)
        return next(res.results).text
```

:::
