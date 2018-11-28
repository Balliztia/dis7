import sys

'''
Example 1: Print numbers in a nested list
Description:
Write a program to print all the numbers in a nested list in a reverse order.
The nested list L is defined recursively:
L = [L1, L2], where L1, L2 can either be an integer or a nested list.
Sample Input:
[[0,1],[2,[3,[4,5]]]]
(+ (+ 1 2) 3)
Sample Output:
5 4 3 2 1 0
'''
def print_nest_list_rec(nlist):
    if type(nlist) == int:
        print(nlist, end=' ')
    else:
        print_nest_list_rec(nlist[1])
        print_nest_list_rec(nlist[0])

def print_nest_list_stack(nlist):
    stack = nlist
    while len(stack)>0:
        a = stack.pop()
        if type(a)==int:
            print(a, end=' ')
        else:
            stack.append(a[0])
            stack.append(a[1])

'''
Example 2: Check parentheses pairs
Description:
Write a program to check if the input parentheses pairs are legal.
Input is a string containing several parentheses pairs.
Sample Input:
'(()())'
'())))'
'((())'
'((('
')))'
Sample Output:
Correct
Wrong
Wrong
Wrong
Wrong
'''
def parentheses_pair_stack(s):
    stack = []
    for c in s:
        if c == '(':
            stack.append(c)
        elif len(stack) == 0:
            print('Wrong')
            return
        else:
            stack.pop()
    if len(stack) == 0:
        print('Correct')
    else:
        print('Wrong')

def parentheses_pair_rec(s):
    def rec(s):
        # s=='' or s=='((' or s==')()'
        if ')' not in s or s[0]!='(':
            return s
        # Recursively remove () from the string
        else:
            if s[1] == ')':
                s = s[2:]
            else:
                s = s[0] + rec(s[1:])
            return rec(s)
    if len(rec(s)) == 0:
        print('Correct')
    else:
        print('Wrong')

'''
Example 3: Seudocode for hm4 tokenizer (stack)
Sample Input:
['(','rotate','(','rotate','(','rotate','(','line','1','2','3','4',')','(','+','1','2',')',')','5',')','5',')']
Sample Output:
['rotate',['rotate',['rotate',['line','1','2','3','4'],['+','1','2']],'5'],'5']
'''
def tokenizer_stack(tokens):
    for all token in tokens:
        if current token is not ')', push token to stack
        if current token is ')':
            pop items from stack until meet one '('
            store all the popped items except '(' to a list L, reverse L
            push L into stack

def tokenizer_rec(tokens):
    input: a list of tokens
    output: a nested list
    when to call: '('
    when to return: ')'
