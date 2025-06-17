

::: {.cell 0=‘h’ 1=‘i’ 2=‘d’ 3=‘e’}

``` python
from nbdev.showdoc import *
```

:::

::: {.cell 0=‘e’ 1=‘x’ 2=‘p’ 3=‘o’ 4=‘r’ 5=‘t’}

``` python
calculator_prompt = """
Your task is to add calls to a Calculator API to a piece of text. The API call should help you get information required to complete the text. \n
You can call the API by writing "Calculator(operation)!" where "operation" is the type of calculation you want to perform. Here are some examples of API calls:

Input: John has 5 apples and his friend gave him 3 more. John now has 8 apples.
Ouput: John has 5 apples and his friend gave him 3 more. John now has [Calculator("5 + 3")] 8 apples.

Input: Jane needs to divide 24 pieces of candy equally among 6 kids. Each kid will get 4 pieces of candy.
Output: Jane needs to divide 24 pieces of candy equally among 6 kids. Each kid will get [Calculator(24 / 6)] 4 pieces of candy.

Input: From this, we have 4 * 30 minutes = 120 minutes.
Output: From this, we have 4 * 30 minutes = [Calculator(4 * 30)] 120 minutes.

Input: {input}
Output:
"""
```

:::

::: {.cell 0=‘e’ 1=‘x’ 2=‘p’ 3=‘o’ 4=‘r’ 5=‘t’}

``` python
qa_prompt = """
Your task is to add calls to a Question Answering API to a piece of text. The questions should help you get information required to complete the text.
You can call the API by writing "[QA(question)]" where "question" is the question you want to ask. Here are some examples of API calls:

Input: Joe Biden was born in Scranton, Pennsylvania.
Output: Joe Biden was born in [QA("Where was Joe Biden born?")] Scranton, [QA("In which state is Scranton?")] Pennsylvania.

Input: Coca-Cola, or Coke, is a carbonated soft drink manufactured by the Coca-Cola Company.
Output: Coca-Cola, or [QA("What other name is Coca-Cola known by?")] Coke, is a carbonated soft drink manufactured by [QA("Who manufactures Coca-Cola?")] the Coca-Cola Company.

Input: {input}
Output:
"""
```

:::

::: {.cell 0=‘e’ 1=‘x’ 2=‘p’ 3=‘o’ 4=‘r’ 5=‘t’}

``` python
wolframe_prompt = """
Your task is to add calls to a Scientific API to a piece of text that related to chemistry, math, physics. The questions should help you get information required to complete the text.
You can call the API by writing "[Wolframe(question)]" where "question" is the question you want to ask. Here are some examples of API calls:

Input: The complex conjugate of 2 + 3i is 2 - 3i.
Output: The complex conjugate of 2 + 3i is [Wolframe("What is the complex conjugate of 2 + 3i")] 2 - 3i.

Input: Solve x^2 + 4x + 6 = 0. The answer is x = -2 - i sqrt(2)
Output: Solve x^2 + 4x + 6 = 0. The answer is [Wolframe("Solve x^2 + 4x + 6 = 0")] x = -2 - i sqrt(2)

Input: Given a sequence of numbers: 21.3, 38.4, 12.7, 41.6. The mean is 28.5
Output: Given a sequence of numbers: 21.3, 38.4, 12.7, 41.6. The mean is [Wolframe("What is the mean of 21.3, 38.4, 12.7, 41.6")] 28.5

Input: {input}
Output:
"""
```

:::
