# 遇到的问题和不明白的函数

# numpy.getfromtext()

data = getfromtext("filepath/file.csv", delimiter=',')
it should be [aaaa, bbbb, cccc, dddd], but actually [nan nan nan nan] 
    
# 这是因为numpy在读取元素时，默认是按照float格式来读取的，对于不能转换为float类型的数据会读取为nan（not a number），对于留空的数据则显示为na（not available），为了正确的读取数据，可以通过增加参数：
# dtype参数用来指定读取数据的格式，这里的U75表示将每一个数据都读取为75个byte的unicode数据格式
data = getfromtext("filepath/file.csv", delimiter=',', dtype=U75)


# pd.read_csv() 
# 利用pandas导入csv

import pandas as pd
data = pd.read_csv(filepath_or_buffer, sep=', ', delimiter=None, header='infer', names=None, )

filepath_or_buffer  文件路径或字符串
sep 分隔符，默认是','，格式为字符串
delimiter sep的替代名称，即也是分隔符
header 数据开始前列名所占的行数，默认值infer把第一行视作列名. 
[header=0, name='age']表示age作为列名，names本身可以是一个列表
header=[1,3,5]时，0,2,4行被忽略

# pandas的drop()函数
可用于删除行、列
drop默认删除行，删除列时需要令axis=1
dataset= dataset.drop('column_name', axis=1) # 删除名为column_name的列
