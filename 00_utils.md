

::: {.cell 0=‘h’ 1=‘i’ 2=‘d’ 3=‘e’}

``` python
from nbdev.showdoc import *
```

:::

::: {.cell 0=‘e’ 1=‘x’ 2=‘p’ 3=‘o’ 4=‘r’ 5=‘t’}

``` python
import yaml
import re
from typing import Optional
```

:::

::: {.cell 0=‘e’ 1=‘x’ 2=‘p’ 3=‘o’ 4=‘r’ 5=‘t’}

``` python
def yaml2dict(file_path):
    with open(file_path,"r") as file:
        data=yaml.safe_load(file)
    return data
```

:::

::: {.cell 0=‘e’ 1=‘x’ 2=‘p’ 3=‘o’ 4=‘r’ 5=‘t’}

``` python
def extract_api_content(text:str,api_name:str)->str:
    """从给定的文本中抽取出api请求"""
    start_tag=f"{api_name}("
    end_tag=")"
    start_idx=text.find(start_tag)
    if start_idx==-1:
        return None
    start_idx+=len(start_tag)
    end_idx=text.find(end_tag,start_idx)
    if end_idx==-1:
        return None
    return text[start_idx:end_idx]
```

:::

::: {.cell 0=‘e’ 1=‘x’ 2=‘p’ 3=‘o’ 4=‘r’ 5=‘t’}

``` python
def extract_api_syntax(text:str,api_name:str)->str:
    """抽取语法"""
    pattern = r"\[{}\(.*?\)\]".format(api_name)
    matches = re.findall(pattern, text)
    return matches
```

:::

::: {.cell 0=‘e’ 1=‘x’ 2=‘p’ 3=‘o’ 4=‘r’ 5=‘t’}

``` python
def extract_api_name(text:str,is_end_token:bool=True)->Optional[str]:
    if is_end_token:
        pattern=r'\[(\w+)\(.+\]\s?'
    else:
        pattern=r'\[(\w+)\(.+\s?'
    match=re.search(pattern,text)
    if match:
        return match.group(1)
    else:
        return None
```

:::
