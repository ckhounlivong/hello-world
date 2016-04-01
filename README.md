# hello-world
Training_201604
Hello this is Catherine from AGD Fr.
Please find the code for the pre work.

"""
@author: c.khounlivong
"""

"""
********************************* PART I **************************************
"""
"""
************************************ A ****************************************
"""
def match_ends(words):
    i=0
    result=0
    while i <len(words):
        ti=len(words[i])
        if len(words[i])>=2 and words[i][0] ==words[i][ti-1]:
            result=result+1
        i=i+1
    return result
    
words=["tata", "toto", "a", "ata", "pap"]
match_ends(words)


"""
***********************************  B ****************************************
"""  
def front_x(words):
    for word in sorted(words):
        newlista = [word for word in sorted(words) if word[0]== "x"]
        newlistb = [word for word in sorted(words) if word[0]!= "x"]
    return newlista + newlistb
    
words=["xin", "apple", "mix", "corner", "xaxa"]
front_x(words)

    
"""
************************************ C  ***************************************
"""
def sort_last(tuples):
    return tuples[-1]

tuples=[(1, 7), (1, 3), (3, 4, 5), (2, 2)]
sorted(tuples, key=sort_last)


"""
*********************************** TEST  *************************************
"""
def test(got, expected):
    if got == expected:
        prefix = ' OK '
    else:
        prefix = '  X '
    print '%s got: %s expected: %s' % (prefix, repr(got), repr(expected))

def main():
    print 'match_ends'
    test(match_ends(['aba', 'xyz', 'aa', 'x', 'bbb']), 3)
    test(match_ends(['', 'x', 'xy', 'xyx', 'xx']), 2)
    test(match_ends(['aaa', 'be', 'abc', 'hello']), 1)

    print
    print 'front_x'
    test(front_x(['bbb', 'ccc', 'axx', 'xzz', 'xaa']),
        ['xaa', 'xzz', 'axx', 'bbb', 'ccc'])
    test(front_x(['ccc', 'bbb', 'aaa', 'xcc', 'xaa']),
        ['xaa', 'xcc', 'aaa', 'bbb', 'ccc'])
    test(front_x(['mix', 'xyz', 'apple', 'xanadu', 'aardvark']),
        ['xanadu', 'xyz', 'aardvark', 'apple', 'mix'])

main()


"""
************************************ D  ***************************************
"""
def remove_adjacent(nums):
    a = []
    for b in nums:
        if len(a):
            if a[-1] != b:
                a.append(b)
        else: a.append(b)
    return a

nums=[1, 2, 2, 3]
remove_adjacent(nums)


"""
************************************ E  ***************************************
"""
def linear_merge(lista, listb):
    listc=lista+listb
    for l in sorted(listc):
        newlistc = [l for l in sorted(listc)]      
    return newlistc
    
lista=['aa', 'xx', 'zz']
listb=['bb', 'cc']
linear_merge(lista, listb)


"""
*********************************** TEST  *************************************
"""
def test(got, expected):
    if got == expected:
        prefix = ' OK '
    else:
        prefix = '  X '
    print '%s got: %s expected: %s' % (prefix, repr(got), repr(expected))
    
def main():
    print 'remove_adjacent'
    test(remove_adjacent([1, 2, 2, 3]), [1, 2, 3])
    test(remove_adjacent([2, 2, 3, 3, 3]), [2, 3])
    test(remove_adjacent([]), [])

    print
    print 'linear_merge'
    test(linear_merge(['aa', 'xx', 'zz'], ['bb', 'cc']),
        ['aa', 'bb', 'cc', 'xx', 'zz'])
    test(linear_merge(['aa', 'xx'], ['bb', 'cc', 'zz']),
        ['aa', 'bb', 'cc', 'xx', 'zz'])
    test(linear_merge(['aa', 'aa'], ['aa', 'bb', 'bb']),
        ['aa', 'aa', 'aa', 'bb', 'bb'])

main()


"""
********************************* PART II *************************************
"""
"""
************************************ A ****************************************
"""
def donuts(count):
    if count <10:
        x= 'Number of donuts: %s' % (repr(count))
    else: x= 'Number of donuts: many'
    return x

donuts(5)
donuts(23)


"""
************************************ B ****************************************
"""
def both_ends(s):
    if len(s)>2:
        t=s[0]+s[1]+s[-2]+s[-1]
    else: t=''
    return t
s='spring'

both_ends(s)


"""
************************************ C ****************************************
"""
def fix_start(s):
    i=1
    t=s
    while i<len(s):
        u=s[i]
        if s[i]==s[0]:
            t=s.replace(u, '*')
        i=i+1
    return s[0]+t[1:len(t)]

s='babbles'
fix_start(s)


"""
************************************ D ****************************************
"""
def mix_up(a, b):
    word1=b[0]+b[1]+a[2:len(a)]
    word2=a[0]+a[1]+b[2:len(b)]
    return word1 + ' ' + word2

a='mix'
b='pod'
c='dog'
d='dinner'

mix_up(a, b)
mix_up(c, d)


"""
*********************************** TEST **************************************
"""
def test(got, expected):
    if got == expected:
        prefix = ' OK '
    else:
        prefix = '  X '
    print '%s got: %s expected: %s' % (prefix, repr(got), repr(expected))

def main():
    print 'donuts'
    # Each line calls donuts, compares its result to the expected for that call.
    test(donuts(4), 'Number of donuts: 4')
    test(donuts(9), 'Number of donuts: 9')
    test(donuts(10), 'Number of donuts: many')
    test(donuts(99), 'Number of donuts: many')

    print
    print 'both_ends'
    test(both_ends('spring'), 'spng')
    test(both_ends('Hello'), 'Helo')
    test(both_ends('a'), '')
    test(both_ends('xyz'), 'xyyz')

  
    print
    print 'fix_start'
    test(fix_start('babble'), 'ba**le')
    test(fix_start('aardvark'), 'a*rdv*rk')
    test(fix_start('google'), 'goo*le')
    test(fix_start('donut'), 'donut')

    print
    print 'mix_up'
    test(mix_up('mix', 'pod'), 'pox mid')
    test(mix_up('dog', 'dinner'), 'dig donner')
    test(mix_up('gnash', 'sport'), 'spash gnort')
    test(mix_up('pezzy', 'firm'), 'fizzy perm')

main()


"""
************************************ D ****************************************
"""
def verbing(s):
    result=''
    t=s[-3:len(s)]
    if len(s)<=3 :
        result=s
    elif len(s)>3 and t=='ing':
        result=s+'ly'
    elif len(s)>3 and t!='ing':
        result=s+'ing'
    return result
    
verbing('sing')
verbing('suit')
verbing('lie')


"""
************************************ E ****************************************
"""   

def not_bad(s):
    result=''
    t='not'
    u='bad'
    result=s.split(t)[-1].split(u)[0]
    if t>u:
        news=s.replace(t+result+u,'good')
    else: news=s
    return news
    
s='This dinner is bad and not ok!'
not_bad(s)
ss='This dinner is not that bad!'
not_bad(ss)


"""
************************************ F ****************************************
""" 
def front_back(a,b):
    if len(a)%2 ==0:
        fronta=a[0:int(len(a)/2)]
        backa=a[int(len(a)/2):]
    elif len(a)%2 !=0:
        fronta = a[0:int(len(a)/2)+1]
        backa = a[int(len(a)/2)+1:]
    if len(b)%2 ==0:
        frontb=b[0:int(len(b)/2)]
        backb=b[int(len(b)/2):]
    elif len(b)%2 !=0:
        frontb = b[0:int(len(b)/2)+1]
        backb = b[int(len(b)/2)+1:]
    return fronta+frontb+backa+backb

a='abcde'
b='fghi'
front_back(a,b)


"""
*********************************** TEST **************************************
"""
def test(got, expected):
    if got == expected:
        prefix = ' OK '
    else:
        prefix = '  X '
    print '%s got: %s expected: %s' % (prefix, repr(got), repr(expected))

def main():
    print 'verbing'
    test(verbing('hail'), 'hailing')
    test(verbing('swiming'), 'swimingly')
    test(verbing('do'), 'do')
    
    print
    print 'not_bad'
    test(not_bad('This movie is not so bad'), 'This movie is good')
    test(not_bad('This dinner is not that bad!'), 'This dinner is good!')
    test(not_bad('This tea is not hot'), 'This tea is not hot')
    test(not_bad("It's bad yet not"), "It's bad yet not")

    print
    print 'front_back'
    test(front_back('abcd', 'xy'), 'abxcdy')
    test(front_back('abcde', 'xyz'), 'abcxydez')
    test(front_back('Kitten', 'Donut'), 'KitDontenut')

main()

"PRE WORK PART II: KAGGLE TITANIC"

"IMPORT TRAIN.CSV"
import csv as csv 
import numpy as np

csv_file_object = csv.reader(open('C:/documents/c.khounlivong/Desktop/Data science for analytics/train.csv', 'rb')) 
header = csv_file_object.next()
                                 
data=[]
for row in csv_file_object:     
    data.append(row)            
data = np.array(data) 	         


"DESCRIPTIVE ANALYTICS TRAIN.CSV"
number_passengers = np.size(data[0::,1].astype(np.float))
number_survived = np.sum(data[0::,1].astype(np.float))
proportion_survivors = number_survived / number_passengers

"GENDER"
women_only_stats = data[0::,4] == "female"
men_only_stats = data[0::,4] != "female"   

women_onboard = data[women_only_stats,1].astype(np.float)     
men_onboard = data[men_only_stats,1].astype(np.float)

proportion_women_survived = \
                       np.sum(women_onboard) / np.size(women_onboard)  
proportion_men_survived = \
                       np.sum(men_onboard) / np.size(men_onboard) 

print 'Proportion of women who survived is %s' % proportion_women_survived
print 'Proportion of men who survived is %s' % proportion_men_survived

"CLASS"
CLASS1_stats = data[0::,2] == "1" 
CLASS_stats = data[0::,2] != "1"

CLASS1_onboard = data[CLASS1_stats,1].astype(np.float)     
CLASS_onboard = data[CLASS_stats,1].astype(np.float)

proportion_CLASS1_survived = \
                       np.sum(CLASS1_onboard) / np.size(CLASS1_onboard)  
proportion_CLASS_survived = \
                       np.sum(CLASS_onboard) / np.size(CLASS_onboard) 

print 'Proportion of CLASS1 who survived is %s' % proportion_CLASS1_survived
print 'Proportion of other CLASS who survived is %s' % proportion_CLASS_survived


"PANDA"
import pandas as pd
import numpy as np

df = pd.read_csv('C:/documents/c.khounlivong/Desktop/Data science for analytics/train.csv', header=0)
df
df.head(3)
df.tail(3)
type(df)
df.dtypes
df.info()
df.describe()

df['Age'][0:10]
df.Age[0:10]
type(df['Age'])
df['Age'].mean()
df[ ['Sex', 'Pclass', 'Age'] ]
df[df['Age'] > 60]
df[df['Age'] > 60][['Sex', 'Pclass', 'Age', 'Survived']]
df[df['Age'].isnull()][['Sex', 'Pclass', 'Age']]

for i in range(1,4):
    print i, len(df[ (df['Sex'] == 'male') & (df['Pclass'] == i) ])


"GRAPH"
import pylab as P
df['Age'].hist()
P.show()

df['Age'].dropna().hist(bins=16, range=(0,80), alpha = .5)
P.show()

df['Gender'] = 4
df['Gender'] = df['Sex'].map( lambda x: x[0].upper() )
df['Gender'] = df['Sex'].map( {'female': 0, 'male': 1} ).astype(int)
df.head()

"REPLACE AGE"
median_ages = np.zeros((2,3))
median_ages
for i in range(0, 2):
    for j in range(0, 3):
        median_ages[i,j] = df[(df['Gender'] == i) & \
                              (df['Pclass'] == j+1)]['Age'].dropna().median()
 
median_ages

df['AgeFill'] = df['Age']
df.head()

df[ df['Age'].isnull() ][['Gender','Pclass','Age','AgeFill']].head(10)
for i in range(0, 2):
    for j in range(0, 3):
        df.loc[ (df.Age.isnull()) & (df.Gender == i) & (df.Pclass == j+1),\
                'AgeFill'] = median_ages[i,j]
                
df['AgeIsNull'] = pd.isnull(df.Age).astype(int)
df['FamilySize'] = df['SibSp'] + df['Parch']

df['Age*Class'] = df.AgeFill * df.Pclass
df.dtypes
df.dtypes[df.dtypes.map(lambda x: x=='object')]


df = df.drop(['Name', 'Sex', 'Ticket', 'Cabin','PassengerId'], axis=1) 
df = df.drop(['Age'], axis=1)

df=df.dropna()
df['Emb'] = df['Embarked'].map( {'S': 0, 'C': 1,'Q':2} ).astype(int)
df = df.drop(['Embarked'], axis=1) 

"DIVIDE TRAIN.CSV INTO TRAINING AND TESTING SET"
import pandas as pd
import numpy as np
from sklearn.cross_validation import train_test_split

train_data, test_data = train_test_split(df, test_size = 0.4)



"RANDOM FOREST"
import pandas as pd
import numpy as np
from sklearn.ensemble import RandomForestClassifier 

train=train_data.as_matrix(columns=None)
test=test_data.as_matrix(columns=None)

forest = RandomForestClassifier(n_estimators = 100)
forest = forest.fit(train[0::,2::],train[0::,0])

output = forest.predict(test[0::,2::])
