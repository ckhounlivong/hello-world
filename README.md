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
