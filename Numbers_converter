import sys



def main():
    print("---------welcome to the numbers converter.")
    print("---------This program will convert any number to its appriprate")
    print("---------equivlance in the other number systems (Binary, Decimal, Ocatdecimal and hexadecimal)")
    print("----------------------------------------------------------------------------------------------------")
    print("please note that:")
    print("1.Those convertions are mostly accurate for number with less than 16 digits including decimals")
    print("2.The numbers are returned as strings so no operations can be done with them")
    print("3.The range of numbers that can be converted is the least for Binary and the most for Hexadecimal")
    print("4.Convert both positive and negative numbers")
    print("5.Some problems may occure if you enter very large numbers (16 digits max)")
    print("----------------------------------------------------------------------------------------------")
    while True:
        try:
            print("Please choose the type of number you want to convert")
            print("(Decimal - 1)\n(Binary - 2)\n(Octadecimal - 3)\n(Hexadecimal - 4)\n(To quit program - 5)")
            user = int(input("Enter number for the approprate type of number: ").strip())
            if user not in [1, 2, 3, 4, 5]:
                print("---------------------------------------------------------------------------------------------------")
                print("please Enter a valid number")
                print("---------------------------------------------------------------------------------------------------")
                continue
        except ValueError:
            print("Please Enter numbers only")
            print("---------------------------------------------------------------------------------------------------")
            continue
        print("---------------------------------------------------------------------------------------------------")
        if user == 1:
            decimal1 = user_input_decimal()
            binary1 = DEC_Bi(decimal1)
            octadeciaml1 = DEC_OCT(decimal1)
            hexadecimal1 = DEC_HEX(decimal1)
            print("---------------------------------------------------------------------------------------------------")
            print(f"Decimal: {decimal1}")
            print(f"Binary: {binary1}")
            print(f"Octadecimal: {octadeciaml1}")
            print(f"Hexadecimal: {hexadecimal1}")
            print("---------------------------------------------------------------------------------------------------")
            input("Press Enter to continue...")
            continue
        elif user == 2:
            binary2 = user_input_binary()
            decimal2 = BI_DEC(float(binary2))
            octadeciaml2 = DEC_OCT(float(decimal2))
            hexadecimal2 = DEC_HEX(float(decimal2))
            print("---------------------------------------------------------------------------------------------------")
            print(f"Decimal: {decimal2}")
            print(f"Binary: {binary2}")
            print(f"Octadecimal: {octadeciaml2}")
            print(f"Hexadecimal: {hexadecimal2}")
            print("---------------------------------------------------------------------------------------------------")
            input("Press Enter to continue...")
            continue
        elif user == 3:
            octadeciaml3 = user_input_octal()
            decimal3 = OCT_DEC(float(octadeciaml3))
            binary3 = DEC_Bi(float(decimal3))
            hexadecimal3 = DEC_HEX(float(decimal3))
            print("---------------------------------------------------------------------------------------------------")
            print(f"Decimal: {decimal3}")
            print(f"Binary: {binary3}")
            print(f"Octadecimal: {octadeciaml3}")
            print(f"Hexadecimal: {hexadecimal3}")
            print("---------------------------------------------------------------------------------------------------")
            input("Press Enter to continue...")
            continue
        elif user == 4:
            hexadecimal4 = user_input_hex()
            decimal4 = HEX_DEC(hexadecimal4)
            binary4 = DEC_Bi(float(decimal4))
            octadeciaml4 = DEC_OCT(float(decimal4))
            print("---------------------------------------------------------------------------------------------------")
            print(f"Decimal: {decimal4}")
            print(f"Binary: {binary4}")
            print(f"Octadecimal: {octadeciaml4}")
            print(f"Hexadecimal: {hexadecimal4}")
            print("---------------------------------------------------------------------------------------------------")
            input("Press Enter to continue...")
            continue
        else:
            sys.exit()




################################# user input Functions ###########################################
def user_input_decimal():
    while True:
        try:
            user = float(input("Enter The number in Decimal: ").strip())
            break
        except ValueError:
            print("Enter a valid Number")
    return user


def user_input_binary():
    valids = ["1", "0", "."]
    neg = False
    while True:
        try:
            flag = False
            user = float(input("Enter The number in Binary: ").strip())
            if str(user)[0] == "-":
                neg = True
                user = float(str(user)[1:])
            for i in str(user):
                if i not in valids:
                    print("Invalid Binary number\nTry again")
                    flag = True
                    break
            if flag:
                continue
            break
        except ValueError:
            print("Enter a valid Number")
    if neg:
        user = float("-" + str(user))
    return user


def user_input_octal():
    invalids = ["8", "9"]
    while True:
        try:
            flag = False
            user = float(input("Enter The number in octadeciaml: ").strip())
            for i in str(user):
                if i in invalids:
                    print("Invalid octadeciaml number\nTry again")
                    flag = True
                    break
            if flag:
                continue
            break
        except ValueError:
            print("Enter a valid Number")
    return user


def user_input_hex():
    valids = ".0123456789ABCDEF"
    neg = False
    while True:
        num_of_dots = 0
        flag = False
        user = input("Enter The number in Hexadecimal: ").strip().upper()
        if user[0] == "-":
            user = user[1:]
            neg = True
        for i in user:
            if i not in valids:
                print("Invalid Hexadecimal number\nTry again")
                flag = True
                break
            if i == ".":
                num_of_dots += 1
        if flag:
            continue
        if num_of_dots > 1:
            print("Invalid number\nTry again")
            continue
        break
    if neg:
        return "-" + user
    return user

            



########################################################################################################
################################# Binary convertions ###################################################
########################################################################################################


#################### converts decimal to binary
def DEC_Bi(n:float):
    # acurate in string format up to 15 digits before decimal 
    # acurate from -65536 to 65536 if you convert the number to integer
    if n == 0:
        return "0"
    neg = False
    if n < 0:
        n = abs(n)
        neg = True
    
    i, f = str(n).split(".")            
    i = convert_int_to_bi(int(i))
    f = convert_float_to_bi(f)
    ans = i + "." + f
    if neg:
        ans = f"-{ans}"
    return ans


def convert_int_to_bi(n:int):
    if n == 0:
        return 0
    bi = ""
    while n > 0:
        r = n % 2
        n = n // 2
        bi = str(r) + bi
    return bi


def convert_float_to_bi(n:int):
    n = float("." + str(n))
    bi = ""
    for i in range(20):
        if n == 0:
            if i == 0:
                return "0"
            break
        n = n * 2
        bi += str(n)[0]
        n -= int(str(n)[0])
    return bi
    

#############################################
################## converts binary to decimal
#############################################

def BI_DEC(n:float):
    # acurate for 15 digit numbers and below (including decimals)
    if n == 0:
        return "0"
    neg = False
    if n < 0:
        n = abs(n)
        neg = True
    i, f = str(n).split(".")
    i = convert_bi_to_int(i)
    f = convert_bi_to_float(f).removeprefix("0.")
    ans = i + "." + f
    if neg:
        return f"-{ans}"
    return ans


def convert_bi_to_int(n:str):
    dec = 0 
    for i,j in enumerate(n[::-1]):
        dec += int(j) * (2 ** i)
    return str(dec)
    

def convert_bi_to_float(n:str):
    dec = 0
    for i,j in enumerate(n, 1):
        dec += int(j) * (0.5 ** i)
    return str(dec)


########################################################################################################
################################# Octadecimal convertions ##############################################
########################################################################################################


#################### converts decimal to octal
def DEC_OCT(n:float):
    # acurate in string format up to 15 digits before decimal 
    if n == 0:
        return "0"
    neg = False
    if n < 0:
        n = abs(n)
        neg = True
    
    i, f = str(n).split(".")            
    i = convert_int_to_oct(int(i))
    f = convert_float_to_oct(f)
    ans = i + "." + f
    if neg:
        ans = f"-{ans}"
    return ans


def convert_int_to_oct(n:str):
    if n == 0:
        return "0"
    oct = ""
    while n > 0:
        r = n % 8
        n = n // 8
        oct = str(r) + oct
    return oct


def convert_float_to_oct(n:str):
    n = float("." + str(n))
    oct = ""
    for i in range(20):
        if n == 0:
            if i == 0:
                return "0"
            break
        n = n * 8
        oct += str(n)[0]
        n -= int(str(n)[0])
    return oct


##############################################
#################### converts octal to decimal
##############################################

def OCT_DEC(n:float):
    # acurate for 16 digit numbers and below (including decimals)
    if n == 0:
        return "0"
    neg = False
    if n < 0:
        n = abs(n)
        neg = True
    i, f = str(n).split(".")
    i = convert_oct_to_int(i)
    f = convert_oct_to_float(f).removeprefix("0.")
    ans = i + "." + f
    if neg:
        return f"-{ans}"
    return ans


def convert_oct_to_int(n:str):
    oct = 0 
    for i,j in enumerate(n[::-1]):
        oct += int(j) * (8 ** i)
    return str(oct)


def convert_oct_to_float(n:str):
    oct = 0
    for i,j in enumerate(n, 1):
        oct += int(j) * (0.125 ** i)
    return str(oct)


########################################################################################################
################################# Hexadecimal convertions ##############################################
########################################################################################################

#################### converts decimal to Hexadecimal
def DEC_HEX(n:float):
    # acurate for 15 digit numbers and below (including decimals)
    if n == 0:
        return "0"
    neg = False
    if n < 0:
        n = abs(n)
        neg = True

    i, f = str(n).split(".")
    i = convert_int_to_hex(int(i))
    f = convert_float_to_hex(f)
    ans = i + "." + f
    if neg:
        return f"-{ans}"
    return ans


def convert_int_to_hex(n:int):
    if n == 0:
        return "0"
    num = {
        10: "A",
        11: "B",
        12: "C",
        13: "D",
        14: "E",
        15: "F"
    }
    hex = ""
    while n > 0:
        r = n % 16
        if r in num:
            r = num[r]
        n = n // 16
        hex = str(r) + hex
    return hex


def convert_float_to_hex(n:int):
    n = float("." + str(n))
    num = {
        10: "A",
        11: "B",
        12: "C",
        13: "D",
        14: "E",
        15: "F"
    }
    hex = ""
    for i in range(20):
        if n == 0:
            if i == 0:
                return "0"
            break
        n = n * 16
        if int(n) in num:
            hex += num[int(n)]
            n -= int(n)
        else:
            hex += str(n)[0]
            n -= int(str(n)[0])
    return hex
        

##############################################
#################### converts octal to decimal
##############################################

def HEX_DEC(n:str):
    if n == "0" or n == "0.0" or n == ".0":
        return "0"
    neg = False
    if n[0] == "-":
        n = n[1:]
        neg = True
    if "." not in n:
        n += ".0"
    i, f = n.split(".")
    i = convert_hex_to_int(i)
    f = convert_hex_to_float(f).removeprefix("0.")
    ans = i + "." + f
    if neg:
        return f"-{ans}"
    return ans


def convert_hex_to_int(n:str):
    hex = 0
    num = {
        "A": 10,
        "B": 11,
        "C": 12,
        "D": 13,
        "E": 14,
        "F": 15
    }
    for i,j in enumerate(n[::-1]):
        if j in num:
            j = int(num[j])
        hex += int(j) * (16 ** i)
    return str(hex)


def convert_hex_to_float(n:str):
    hex = 0
    num = {
        "A": 10,
        "B": 11,
        "C": 12,
        "D": 13,
        "E": 14,
        "F": 15
    }
    for i, j in enumerate(n, 1):
        if j in num:
            j = int(num[j])
        hex += int(j) * (0.0625 ** i)
    return str(hex)


if __name__ == "__main__":
    main()
