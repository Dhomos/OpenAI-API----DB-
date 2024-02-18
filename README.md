# OpenAI-API-DBConverter
這是使用LangChain串接OpenAI API的實驗性小工具：
網頁再造案時常會有DB表格及欄位名稱重新命名的需求，
然而翻寫SQL語句時，要對照新舊名稱非常耗時且浪費人力，
故建立此工具讓OpenAI對SQL語句自動進行轉換。

# 使用方式
Step1.需訂閱OpenAI API服務，並且提供API KEY給轉換器
Step2.提供轉換器新舊DB名稱的參考對照表(請參照DataRewriteExample.csv)
Step3.開始執行轉換器，並輸入欲轉換之SQL語句。
      轉換器將解析SQL語句之表格名稱及屬於該表格下之欄位名稱，
      隨後至對照表中找出對應之新表格及新欄位名稱，
      並將SQL語句進行轉換為新名稱之寫法。

ex.

INPUT:
" select  s_filenm 	from GSO..c60_att with (nolock) 		where crtid = #crtid#   and sys = #sys#  and c_no = #c_no#    and s_file = #s_file#"

OUTPUT:
"select  SUIT_FILE_NM  FROM  CASE_ATT  WITH  (NOLOCK)  WHERE CRT_ID = #crtid#  AND SYS = #sys#  AND CASE_NO = #c_no# AND SUIT_FILE = #s_file"


