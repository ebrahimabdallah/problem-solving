```
#include<iostream>
#include<vector>
using namespace std;
 
 
long long calcutar(long long a1, long long an, long long  n)
{
	return ((a1 + an)* n) / 2;
}
int main()
{
   
	int t;
	cin >> t;
	while (t--)
	{
		long long  n;
		cin >> n;
		long long result = calcutar(1, n, n);
		vector<long long> power;
		power.push_back(1);
		for (int i = 1; i < 32; i++)
		{
			power.push_back(power[i - 1] * 2);
		}
		long long sum = 0;
		for (int i = 0; i < 32; i++)
		{
			if (power[i] <= n)
			{
				sum += power[i];
			}
		}
			result -= sum;
			result -= sum;
			cout << result << endl;
		}
 
 
	}
	
 
```
