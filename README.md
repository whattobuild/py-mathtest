# py-mathtest
A tool that can randomly generates simple add and subtract questions.
一个用来生成简单加减法数学题目的Python程序

包安装方法：
pip3 install pymathtest


使用方法：
命令行形式：
>python3 simple_maths_questions.py
获取帮助信息：
>python3 simple_maths_question.py -h
usage: simple_maths_questions.py [-h] [-q QUANTITY] [-m MIN_NUMBER] [-x MAX_NUMBER] [-n NUMBER] [-w] [-g]

生成指定数量的简单加减法数学题

optional arguments:
  -h, --help            show this help message and exit
  -q QUANTITY, --quantity QUANTITY
                        生成题目的数量，默认为20,最多200题
  -m MIN_NUMBER, --min_number MIN_NUMBER
                        题目中出现的最小数字，默认为1
  -x MAX_NUMBER, --max_number MAX_NUMBER
                        题目中出现的最大数字，默认为50
  -n NUMBER, --number NUMBER
                        算式由多少个数字构成，默认为2
  -w, --with_answer     生成显示答案的试题
  -g, --negative        允许在算式和运算结果中出现负数，不加该选项时为不允许。


包引用使用方法：
from pymathtest import simple_maths_question as smq
其中最主要两个用到的函数是：gen_questions和gen_question_with_answers，详情请见下面帮助文档。



NAME simple_maths_questions - # --coding: utf-8 --

FUNCTIONS format_a_number(num) 格式化数字的显示方式，如果是负数，在数字的两边加上()

gen_one_question(min_number, max_number, num_of_numbers)
    生成一道题目
    
    :param min_number: int型，算式中允许出现的最小数字
    :param max_number: int型，算式中允许出现的最大数字
    :param num_of_numbers: int型，组成算式的数字数量
    :return: 结果list

gen_one_question_not_negative(min_number, max_number, num_of_numbers)
    生成一道非负结果的测试题目
    
    保证算式中的数字和计算结果都不为负数。
    
    :param min_number: int型，算式中允许出现的最小数字
    :param max_number: int型，算式中允许出现的最大数字
    :param num_of_numbers: int型，组成算式的数字数量
    :return: 结果list

gen_operation_symbol()
    随机生成运算符号
    
    随机生成'+'或'-'，用于构建题目中的算式。
    
    :return: str: 生成的运算符号

gen_question_with_answers(min_number, max_number, num_of_numbers, the_quantity, negative_flag)
    生成包含答案的指定数量的题目
    
    :param min_number: int型，算式中允许出现的最小数字
    :param max_number: int型，算式中允许出现的最大数字
    :param num_of_numbers: int型，组成算式的数字数量
    :param the_quantity: int型，生成的测试题目数量
    :param negative_flag: 题目中是否允许出现负数的标志
    :return: 生成包含答案的题目dict，key：题目， value：答案

gen_questions(min_number, max_number, num_of_numbers, the_quantity, negative_flag)
    生成指定数量的题目
    
    :param min_number: int型，算式中允许出现的最小数字
    :param max_number: int型，算式中允许出现的最大数字
    :param num_of_numbers: int型，组成算式的数字数量
    :param the_quantity: int型，生成的测试题目数量
    :param negative_flag: 题目中是否允许出现负数的标志
    :return: 生成的题目list

main(min_number, max_number, num_of_numbers, the_quantity, negative_flag, display_answer)

trim_parameters(first_num, second_num, num_of_nums, the_quantity, negative, bottom_limit, top_limit, number_limit)
    对用来生成算式的参数进行剪裁
    
    使得各参数合法，并且不会造成过大计算负载。
    
    :param first_num: int型，算式中允许出现的最小或最大数字
    :param second_num: int型，算式中允许出现的最小或最大数字
    :param num_of_nums: int型，组成算式的数字数量
    :param the_quantity: int型，生成的题目数量，最小值为1，最大值为常量MAX_QUANTITY所规定数值
    :param negative: 是否允许出现负数的标志
    :param bottom_limit: int型，算式中允许出现的最小数字的下限，最小不能小于常量MIN_NUMBER_LIMIT所规定数值
    :param top_limit: int型，算式中允许出现的最大数字的上限，最大不能大于常量MAX_NUMBER_LIMIT所规定数值
    :param number_limit: int型，组成算式的数字数量上限，最大不能大于常量MAX_NUMBER_OF_NUMBERS所规定数值
    :return: tuple，经过剪裁后合法的参数：最小数字，最大数字，组成算式的数字数量，题目数量
DATA MAX_NUMBER_LIMIT = 100000 MAX_NUMBER_OF_NUMBERS = 5 MAX_QUANTITY = 200 MIN_NUMBER_LIMIT = -100000
