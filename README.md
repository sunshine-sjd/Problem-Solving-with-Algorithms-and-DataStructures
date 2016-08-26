# Problem-Solving-with-Algorithms-and-DataStructures
Note learning process


1.最大公约数：
-----

欧几里德算法又称辗转相除法， 用于计算两个整数a, b的最大公约数。其计算原理依赖于下面的定理：
定理： gcd(a, b) = gcd(b, a mod b)

    class Fraction:   

        def __init__(self, top, bottom):
            self.num = top
            self.deco = bottom
        
        def __repr__(self):
            return str(self.num) + "/" + str(self.deco)
        
        def __add__(self, other):
            new_num = self.num * other.deco + self.deco * other.num
            new_deco = self.deco * other.deco
            if new_num > new_deco:       
                gcd_num = new_deco
                gcd_deco = new_num
            else:
                gcd_num = new_num
                gcd_deco = new_deco
            while gcd_deco % gcd_num != 0:
                gcd_deco, gcd_num = gcd_num, gcd_deco % gcd_num
            print gcd_num
        return Fraction(new_num/gcd_num, new_deco/gcd_num)  


2. 寻找列表里的最小数:
----
O(n2)和O(n)复杂度的比较


    def find_mininum_in_list_02(ToUsedList):
        mininum = ToUsedList[0]
        for i in ToUsedList:
            if mininum > i:
                mininum = i
        return mininum

    def find_mininum_in_list_01(ToUsedList):
        mininum = ToUsedList[0]
        for i in ToUsedList:
            ismininum = True
            for j in ToUsedList:
                if i > j:
                    ismininum = False
            if ismininum:
                mininum = i
        return mininum
    
3.infinite monkey theorem:
----
    import random,string

    # shakespeare = 'methinks it is a weasel'
    shakespeare = 'abc'
    quoteLen = len(shakespeare)


    def generate():
        char = string.ascii_lowercase+' '
        randchars = ''.join(random.choice(char) for _ in range(quoteLen))
        return randchars


    def score():
        scorenum = 0
        randchars = generate()
        shake = shakespeare.split()
        randlist = randchars.split()
        for i,j in zip(shake,randlist):
            if i==j:
               scorenum += 1
        scorecount = (scorenum / quoteLen) * 100
        return scorecount

    def main():
        run = 0
        curScore = 0
        while not(curScore == 100):
            curScore = score()
            if curScore != 0:
                print(run, " = ", curScore)
            run += 1

    if __name__ == '__main__':
        main()
