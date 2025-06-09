# 재귀함수(Recursion Function)

## 재귀함수란

### 개념

재귀함수는 함수 안에서 자신의 함수를 다시 호출하는 함수를 의미합니다. 재귀함수는 자신의 로직을 내부적으로 반복하다가, 일정한 조건이 만족되면 함수를 이탈하여 종료하게 됩니다.

재귀함수는 큰 문제를 작은 부분문제로 나눠서 풀 때 사용합니다.  

재귀함수를 사용할 때는 반드시 기저사례(종료 조건)가 있어야 하며, 사이클이 있어 무한히 호출하는 경우를 주의하여 사용하여야 합니다.



점화식 





###  재귀함수를 사용한 사례

피보나치 수열

```c++
#include <bits/stdc++.h>
using namespace std;
int fibo(int n)
{
    cout << n << endl;
    if (n == 0 || n == 1)
        return n;
    return fibo(n - 1) + fibo(n - 1);
}
int main()
{
    cout << fibo(4) << endl;
}

```



c++에서의 순열 next_permutation

```c++
#include <bits/stdc++.h>

using namespace std;

int main()

{

    int a[] = {3, 2, 1};  

    sort(&a[0], &a[0] + 3);

    do

    {

        for (int i : a)

            cout << i << " ";

        cout << '\n';

		  } while (next_permutation(&a[0], &a[0] + 3));

}
```



재귀 함수로 순열

```c++
#include <bits/stdc++.h>
using namespace std;

vector<int> v = {1, 2, 3};
void printV(vector<int> &v)
{
    for (int i = 0; i < v.size(); i++)
    {
        cout << v[i] << " ";
    }
    cout << '\n';
}
void makePermutation(int n, int r, int depth)
{
    cout << n << " : " << r << " : " << depth << '\n';
    if (r == depth)
    {
        printV(v);
        return;
    }
    for (int i = depth; i < n; i++)
    {
        swap(v[i], v[depth]);
        makePermutation(n, r, depth + 1);
        swap(v[i], v[depth]);
    }
    return;
}

int main()
{
    makePermutation(3, 3, 0);
}
```

조합 재귀함수

```c++
#include <bits/stdc++.h>
using namespace std;

int n = 5, k = 3, a[5] = {1, 2, 3, 4, 5};
void print(vector<int> b)
{
    for (int i : b)
        cout << i << " ";
    cout << '\n';
}

void combi(int start, vector<int> b)
{

    if (b.size() == k)
    {
        print(b);
    }
    for (int i = start + 1; i < n; i++)
    {
        b.push_back(i);
        combi(i, b);
        b.pop_back();
    }
    return;
}
int main()
{
    vector<int> b;
    combi(-1, b);
    return 0;
}
```

Split 구현

```c++
#include <bits/stdc++.h>
using namespace std;

vector<string> split(const string &input, string delimeter)
{
    auto start = 0;
    auto end = input.find(delimeter);
    vector<string> result;
    while (end != string::npos)
    {
        result.push_back(input.substr(start, end - start));
        start = end + delimeter.size();
        end = input.find(delimeter, start);
    }
    result.push_back(input.substr(start));
    return result;
}

int main()
{
    string s = "hi, my name, is , tam";
    vector<string> x = split(s, ",");
    for (const string &z : x)
    {
        cout << z;
    }
}
```



array to decay



중복된 요소를 삭제 - map으로 

```c++
// Online C++ compiler to run C++ program online
#include <bits/stdc++.h>
using namespace std;

map<int, int> mp;
int main()
{
    vector<int> v{1, 1, 2, 3, 3};

    for (int i : v)
    {
        if (mp[i])
            continue;
        else
            mp[i] = 1;
    }

    vector<int> ret;
    for (auto it : mp)
        ret.push_back(it.first);

    for (auto x : ret)
        cout << x << endl;

    return 0;
}
```

중복된 요소를 삭제 - unique

```c++
// Online C++ compiler to run C++ program online
#include <bits/stdc++.h>
using namespace std;

map<int, int> mp;
int main()
{
    vector<int> v{1, 1, 2, 2, 3, 3, 4, 4, 5, 5, 5, 1};

    for (auto x : v)
        cout << x << ' ';
    cout << '\n';

    auto it = unique(v.begin(), v.end());

    cout << it - v.begin() << endl;

    for (auto x : v)
        cout << x << ' ';
    cout << '\n';

    return 0;
}
```

unique 함수는 앞에서 부터 비교하여 뒤로 미룸... 그렇기에 오름차순 정렬이 선행되어야 함.

```c++
// Online C++ compiler to run C++ program online
#include <bits/stdc++.h>
using namespace std;

map<int, int> mp;
int main()
{
    vector<int> v{1, 1, 2, 2, 3, 3, 4, 4, 5, 5, 5, 1, 2};

    for (auto x : v)
        cout << x << ' ';
    cout << '\n';
    sort(v.begin(), v.end());
    auto it = v.erase(unique(v.begin(), v.end()), v.end());

    cout << it - v.begin() << endl;

    for (auto x : v)
        cout << x << ' ';
    cout << '\n';

    return 0;
}
```



```c++
// Online C++ compiler to run C++ program online
#include <bits/stdc++.h>
using namespace std;

typedef long long ll;
int a[100004], b, c, psum[100004], n, m;

int main()
{
    // PrefixSum 누적합 ->정적 배열
    // 구간 쿼리
    // A -> B
    ios_base::sync_with_stdio(false);
    cin.tie(NULL);
    cout.tie(NULL);
    cin >> n >> m;
    for (int i = 1; i <= n; i++)
    {
        cin >> a[i];
        psum[i] = psum[i - 1] + a[i];
    }

    for (int i = 0; i < m; i++)
    {
        cin >> b >> c;
        cout << psum[c] - psum[b - 1] << "\n";
    }
    return 0;
}
```

구현

```c++
// Online C++ compiler to run C++ program online
#include <bits/stdc++.h>
using namespace std;

string dopa = "abcde";
int n, temp;
int sum;
vector<int> v;
void print(string txt)
{
    cout << txt << "\n";
}

int main()
{
    // 앞에서부터 3개의 문자열을 출력하라
    string dopa2 = dopa.substr(0, 3);
    print(dopa2);

    // 해당 문자열을 거꾸로 출력하라.
    reverse(dopa2.begin(), dopa2.end());
    print(dopa2);

    // 거꾸로도니 해당 문자열 끝에 "umzunsik"이란 문자열을 추가하라
    dopa2 += "umzumsik";
    print(dopa2);

    cin >> n;
    for (int i = 0; i < n; i++)
    {
        cin >> temp;
        sum += temp;
        v.push_back(temp);
    }

    sort(v.begin(), v.end());
    for (int i : v)
        cout << i << " ";
    cout << "\n";
    cout << fixed << setprecision(2) << (sum / n);

    return 0;
}
```

