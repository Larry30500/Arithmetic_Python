<h1 align="center">
  <br>
  [指定專題作品] 四則運算 (Python應用)
</h1>


## 目錄
* [摘要](#摘要)
* [重點程式碼說明](#重點說明)
* [系統環境](#系統環境)
* [聯絡資訊](#聯絡資訊)
* [致謝](#致謝)
* [權限](#權限)


## 摘要
### 1. 本作品具有「四則運算、次方運算及小括號之改變運算順序」的數學運算功能。
### 2. 使用者輸入資料時，系統會檢測並刪除多餘的空格，最後再進行數學運算。
### 3. 將輸出結果，寫入至輸出結果檔 (output_result.txt)，最後加以讀取並顯示其輸出結果。

![arithmetic_python](images/arithmetic_python.gif)

<strong><em>假使想要更加了解此程式的話，請參考本頁面底部之作者的聯絡方式。</em></strong>
<br><br>


## 重點程式碼說明
### 按照數學理論上的運算順序，加以定義「加、減、乘、除、次方 和 小括號之改變運算順序」的處理函式。
  ```python
  # 預先查看運算式的下一個字元。
  def peek():
    ⋮
    
  # 取出下一個字元。
  def get():
    ⋮
    
  # 當下一個字元為數字時，回傳數字 或 乘以 10 再回傳結果。
  def number():
    result = int(get()) - 0

    if peek() is None: return result
    else:
      while '0' <= peek() <= '9':
        ⋮
        
    return result

  # 當下一個字元為【(】、【)】、【-】字元時，則處理小括號當中的運算元，或是負號後面的運算元。
  def factor():  
    if '0' <= peek() <= '9':
      return number()

    elif peek() == '(':
      ⋮
      
      return result

    elif peek() == '-':
      ⋮
      
      return -factor()

    return 0

  # 當下一個字元為【x】、【X】、【^】字元時，則處理【x】、【X】、【^】後面的運算元。
  def term():
    result = factor()

    while peek() != None and peek() in '*xX^/':
      current_char = get()

      if current_char in '*xX':
        ⋮
        
      elif current_char == '^':
        ⋮
        
      else:
        ⋮
        
    return result;

  # 當下一個字元為【+】、【-】字元時，則處理【+】、【-】後面的運算元。
  def expression():
    result = term()

    while peek() != None and peek() in '+-':
      if peek() == '+':
        ⋮
        
      else:
        ⋮
        
    return result;
  ```


### 如下的主程式，可將輸出結果，寫入至輸出結果檔 (output_result.txt) 裡面。
  ```python
  f = open('output_result.txt', 'w', encoding = 'utf-8')
  
  print('----------\n')
  f.write('----------\n\n')

  while True:
    input_expression = input('請輸入四則運算式：')
    
    f.write('請輸入四則運算式：')
    
    print(f'\n您輸入的四則運算式為：{input_expression}')
    f.write(f'\n您輸入的四則運算式為：{input_expression}')

    # 輸入 Q 或 q 字元，則退出程式。
    if input_expression.lower() == 'q':
      print('選擇退出，下次再見！！')
      f.write('選擇退出，下次再見！！')
      break

    r = p = 0
    available_characters = '1234567890+-*/xX^() '

    for p in range(len(input_expression)):
      # 判別：如果輸入未允許的字元，則 r 等於 1。
      if input_expression[p] not in available_characters:
        r = 1
        break

    # 判別：如果 r 等於 1，則輸出錯誤訊息。
    if r == 1:
      print('輸入錯誤，請重新輸入。')
      f.write('輸入錯誤，請重新輸入。')

    # 判別：如果輸入皆為允許字元，則輸出運算結果。
    else:
      # 去除輸入字串中的空格。
      spaces_removed_expression = re.sub(' ', '', input_expression)
      # 計算空格的數量。
      space_amout = len(input_expression) - len(spaces_removed_expression)

      copied_expression = spaces_removed_expression
      expression_to_parse = list(spaces_removed_expression)

      # 開始運算。
      result = expression()

      print('您所輸入的空格數量：{space_amout}\n 調整後的四則運算式與計算結果：{copied_expression} = {result}', end = '\n\n')
      print(f'----------', end = '\n\n')
      
      f.write('您所輸入的空格數量：{space_amout}\n 調整後的四則運算式與計算結果：{copied_expression} = {result}', end = '\n\n')
      f.write(f''----------\n\n')

  f.close()
  ```


### 讀取並顯示其輸出結果檔的內容
  ```python
  print('以下將讀取其輸出結果檔，並其顯示內容：')
  
  f = open('output_result.txt', 'r', encoding = 'utf-8')
  ⋮
  
  print('輸出結果檔的內容已經被讀取完畢')
  ```



## 系統環境
### 本程式所在作業系統
* OS：Windows 7 / 10 (Mac OS、Linux 系統亦可相容)

### 相關套件
* Python 核心：3.10


## 聯絡資訊
👤 **Larry Jhuang**
  * Email: larry30500@gmail.com


## 致謝
*非常感謝指導老師 (Francesco Ke) 提供程式設計的靈感和方向，並充分教導程式設計的注意事項和相關細節。*

*如果您喜歡此專案，記得點擊⭐️支持作者。*


## 權限
目前設定為 MIT 權限。請參閱 `LICENSE`，了解更多相關 MIT 權限的規定。

<br><br>[返回目錄](#目錄)
