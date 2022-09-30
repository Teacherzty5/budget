 #include <iostream>
#include <algorithm>
using namespace std;

const int N = 300010;
int s[30][30010];
int n, m;
int v[N], p[N];
int main() {
    cin >> m >> n;
    for (int i = 1; i <= n; i++) {
        cin >> v[i] >> p[i];
        p[i] *= v[i];
    }

    for (int i = 1; i <= n; i++) {
        for (int j = 1; j <= m; j++) {
            s[i][j] = s[i - 1][j];
            if (j >= v[i]) s[i][j] = max(s[i][j], s[i - 1][j - v[i]] + p[i]);
        }
    }
    cout << s[n][m];
    return 0;
}
