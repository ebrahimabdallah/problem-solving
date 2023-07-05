Amugae has a hotel consisting of 10
 rooms. The rooms are numbered from 0
 to 9
 from left to right.

The hotel has two entrances — one from the left end, and another from the right end. When a customer arrives to the hotel through the left entrance, they are assigned to an empty room closest to the left entrance. Similarly, when a customer arrives at the hotel through the right entrance, they are assigned to an empty room closest to the right entrance.

One day, Amugae lost the room assignment list. Thankfully Amugae's memory is perfect, and he remembers all of the customers: when a customer arrived, from which entrance, and when they left the hotel. Initially the hotel was empty. Write a program that recovers the room assignment list from Amugae's memory.

Input
The first line consists of an integer n
 (1≤n≤105
), the number of events in Amugae's memory.

The second line consists of a string of length n
 describing the events in chronological order. Each character represents:

'L': A customer arrives from the left entrance.
'R': A customer arrives from the right entrance.
'0', '1', ..., '9': The customer in room x
 (0
, 1
, ..., 9
 respectively) leaves.
It is guaranteed that there is at least one empty room when a customer arrives, and there is a customer in the room x
 when x
 (0
, 1
, ..., 9
) is given. Also, all the rooms are initially empty.

*input
8
LLRL1RL1

*output
1010000011



------------------------------------------------
# sol 1
#include <iostream>
#include<queue>
using namespace std;
 
int main() {
	deque<int>q(10, 0);
	int n;
	cin >> n;
	while (n--)
	{
		char str;
		cin >> str;
 
 
		if (str == 'L')
 
		{
			for (int i = 0; i < 10; i++)
			{
 
 
				if (q[i] == 0)
				{
					q[i] = 1;
 
					break;
				}
			}
		}
		else if (str == 'R') {
 
			for (int i = 9; i >= 0; i--)
			{
				if (q[i] == 0)
				{
					q[i] = 1;
 
 
					break;
				}
			}
		}
		else
		{
			q[str - '0']=0;
 
		}
	}
	for (int i = 0; i < 10; i++)
	{
		cout << q[i];
	}
	return 0;
}
-----------------------------------------
# sol 2

#include <iostream>
 
using namespace std;
 
int main() {
    string ss, s = "0000000000";
    int n;
    cin >> n >> ss;
    for (int i = 0; i < n; i++) {
        if (ss[i] == 'L') {
            s[s.find_first_of('0')] = '1';
        }
        else if (ss[i] == 'R') {
            s[s.find_last_of('0')] = '1';
        }
        else {
            int b = ss[i] - '0';
            s[b] = '0';
        }
    }
    cout << s << endl;
    return 0;
}
-------------------------------------------------------
# sol 3
#define LL long long
#include<iostream>
using namespace std;
int n, a[10];
string s;
int main()
{
	cin >> n >> s;
	for (int i = 0;i < n;i++)
	{
		if (s[i] == 'L')
		{
			for (int j = 0;j < 10;j++)
				if (!a[j])
				{
					a[j] = 1;
					break;
				}
		}
		else if (s[i] == 'R')
		{
			for
				(int j = 9;j >= 0;j--)
				if (!a[j])
				{
					a[j] = 1;
					break;
				}
		}
		else a[s[i] - '0'] = 0;
	}
	for (int i = 0;i < 10;i++)
	{
		cout << a[i];
	}
}

