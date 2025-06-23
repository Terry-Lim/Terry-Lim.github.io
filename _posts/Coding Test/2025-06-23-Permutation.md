#  순열 (permutation)

## 📌 순열이란

순열은 말 그대로 순서대로 배열한다는 의미를 갖습니다. 모집합에서 **임의의 n개를 순서 가지고 뽑는 것**을 **순열**이라고 합니다. 서로 다른 n개에서 r개를 택하여 배열하는 경우의 수를 **순열의 수**라고 하며 기호로는 **$^nP_r** 로 표현합니다. 이는 **$^nP_r = \frac{n!}{(n - r)!}$** 으로 계산할 수 있습니다.

## ✅ C++에서의 Permutation 

### next_permutation

next_permutaion은 **오름차순인 배열**을 순열하는 함수입니다. 반대로 내림차순인 배열을 순열하는 함수는 prev_permutation입니다.

```c++
#include <bits/stdc++.h>

using namespace std;

int main()

{

    int a[] = {3, 2, 1};  

    sort(&a[0], &a[0] + 3); // 오름차순으로 정열이 선행되어야 합니다.

    do

    {

        for (int i : a)

            cout << i << " ";

        cout << '\n';

		  } while (next_permutation(&a[0], &a[0] + 3)); // next_permutation(시작 주소값, 끝 주소값)

}
```

### 재귀함수로 만드는 순열

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

