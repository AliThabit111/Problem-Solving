# مجموعة المسائل المحلولة (C++)

---

## 1. Petya and Strings
مقارنة سلسلتين نصيتين بدون اعتبار لحالة الأحرف (case-insensitive).

```cpp
#include <iostream>
#include <string>
#include <cctype>
using namespace std;
int main (){
    string s1 , s2;
    cin >> s1 >> s2;
    for (int i=0; i<s1.length();i++){
        s1[i]=tolower(s1[i]);
    }
    for(int j=0; j<s2.length();j++){
        s2[j]=tolower(s2[j]);
    }
    if ( s1 < s2 ){
        cout << "-1" <<endl;
    }
    else if ( s1 > s2 ){
        cout << "1" <<endl;
    }
    else {
        cout << "0"  <<endl;
    }
    return 0;
}
```

---

## 2. Gender (Codeforces - determine gender by distinct letters)
تحديد الجنس بناءً على عدد الحروف المميزة في اسم المستخدم.

```cpp
#include <iostream>
#include <set>
#include <string>
using namespace std;
int main (){
    string  name;
    cin >> name;
    set<char> myset;
    for (int i=0;i < name.length(); i++){
        myset.insert(name[i]);
    }
    if (myset.size() % 2 == 0 ){
        cout << "CHAT WITH HER!" <<endl;
    }
    else {
        cout << "IGNORE HIM!" << endl;
    }
    return 0;
}
```

---

## 3. Xenia and Ringroad (ترتيب الأرقام 1، 2، 3)
إعادة ترتيب مجموع أرقام 1، 2، 3 بحيث يكون تصاعديًا.

```cpp
#include <iostream>
using namespace std;
int main(){
    int count1 =0 , count2 =0 , count3 =0;
    string S;
    cin >> S;
    for(int i=0;i<S.length();i++){
        if(S[i] == '1'){
            count1++;
        }
        else if (S[i] == '2'){
            count2++;
        }
        else if (S[i] == '3'){
            count3++;
        }
    }
    bool first = true;
    for (int j=0; j < count1;j++){
        if (first){ cout << 1; first = false; }
        else { cout << '+' << 1; }
    }        
    for (int k=0; k < count2; k++){
        if(first){ cout << 2; first = false; }
        else { cout << '+' << 2; }
    }
    for (int l=0; l<count3;l++){
        if(first){ cout << 3; first = false; }
        else { cout << '+' << 3; }
    }
    return 0;
}
```

---

## 4. Xenia the Beginner Mathematician
حساب مجموع القيم المرتبة تصاعديًا (سلسلة أرقام 1، 2، 3 - نفس فكرة السابقة تقريبًا لكن بصيغة مختلفة).
> ملاحظة: هذه المسألة استُخدم فيها نفس منطق العد والفرز السابق.

---

## 5. Capitalization
جعل أول حرف من الكلمة كابيتال فقط.

```cpp
#include <iostream>
#include <string>
#include <cctype>
using namespace std;
int main (){
    string S;
    cin >> S;
    S[0] = toupper(S[0]);
    cout << S;
}
```

---

## 6. Bear and Bathroom (Limak and Bob weights)
حساب عدد السنين حتى يصبح وزن ليماك أكبر من بوب.

```cpp
#include <iostream>
using namespace std;
int main(){
    int a,b;
    int y = 0;
    cin >> a >> b;
    while (a <= b){
        a *= 3;
        b *=2;
        y++;
    }
    cout << y;
}
```

---

## 7. Elephant
حساب أقل عدد خطوات ليصل الفيل لصديقه (خطوات من 1 إلى 5).

```cpp
#include <iostream>
using namespace std;
int main (){
    int x;
    int steps;
    cin >> x;
    steps = x / 5;
    if (x % 5 > 0) {
        steps++;
    }
    cout << steps;
}
```

---

## 8. Stones (Neighboring stones different colors)
حساب أقل عدد أحجار يجب إزالتها بحيث لا يتجاور حجران بنفس اللون.

```cpp
#include <iostream>
#include <string>
using namespace std;
int main () {
    int n = 0;
    int count = 0;
    string s;
    cin >> n >> s;
    for (int i = 1 ; i < s.length(); i++)
    {
       if (s[i] == s[i-1])
       {
        count++;
       }
    }
    cout << count;
}
```

---

## 9. Bananas (Soldier buying bananas)
حساب المبلغ الذي يجب اقتراضه لشراء w موزة بأسعار متزايدة.

```cpp
#include <iostream>
using namespace std;
int main (){
    int k , n , w;
    cin >> k >> n >> w;
    int result = k * w*(w+1)/2 ;
    if (result > n)
    {
        cout << result - n << endl;
    }
    else {
        cout << 0 << endl;
    }
    return 0;
}
```

---

## 10. Balanced Parentheses (باستخدام Stack)
التأكد من أن الأقواس في تعبير معين متوازنة.

```cpp
#include <iostream>
#include <stack>
#include <string>
using namespace std;

bool arePair(char open, char close)
{
    if (open == '('&& close == ')')
        return true;
    else if (open == '[' &&  close == ']')
        return true;
    else if (open == '{' && close == '}')
        return true;
    return false;             
}
bool areBalanced(string exp)
{
    stack<char>s;
    for (size_t i = 0; i < exp.length(); i++)
    {
        if (exp[i]=='(' || exp[i]=='{' || exp[i]=='[')
        {
            s.push(exp[i]);
        }
        else if (exp[i]==')' || exp[i]=='}' || exp[i]==']')
        {
            if (s.empty() || !arePair(s.top(), exp[i]))
                return false;
            else
                s.pop();
        }
    }
    return s.empty();
}
int main (){
    string expression;
    cout << "Enter an expression";
    cin >> expression;
    if(areBalanced(expression))
        cout << "Balanced\n";
    else   
        cout << "Not Balanced\n";
}
```

---

## 11. Petya and Vowels
حذف حروف العلة، إضافة نقطة قبل كل حرف ساكن، وتحويل كل الحروف الساكنة لصغيرة.

```cpp
#include <iostream>
#include <string>
#include <cctype>
using namespace std;
int main (){
    string w;
    cin >> w;
    for (size_t i = 0; i < w.length();i++)
    {
        char c = tolower(w[i]);
        if (c == 'a' || c == 'o' || c == 'e' || c == 'i'|| c == 'u' || c == 'y')
        {
            continue;
        }
        else 
        {
            cout << '.' << c;
        }
    }
    return 0;
}
```

---

## 12. Register (Uppercase/Lowercase word conversion)
تحويل الكلمة بالكامل إلى صغيرة أو كبيرة حسب أغلبية الحروف.

```cpp
#include <iostream>
#include <string>
#include <cctype>
using namespace std;
int main (){
    string S;
    int countUpper = 0;
    int countLower = 0;
    cin >> S;
    for(size_t i = 0; i < S.length();i++)
    {
        if (isupper(S[i]))
        {
            countUpper++;
        }
        else 
        {
            countLower++;
        }
    }
    for(size_t j = 0; j < S.length();j++){
        if (countUpper <= countLower)
        {
            S[j] = tolower(S[j]);
        }
        else 
        {
            S[j] = toupper(S[j]);
        }
    }
    cout << S;
    return 0;
}
```

---

## 13. Tanya and Subtraction
تطبيق عملية طرح خاصة (طرح 1 أو قسمة على 10) k مرة.

```cpp
#include <iostream>
using namespace std;
int main (){
    int k , n ;
    cin >> n >> k ;
    for( int i = 0; i < k;i++)
    {
        if(n % 10 == 0){
            n /= 10;
        }
        else
        {
            n -= 1;
        }
    }
    cout << n;
    return 0;
}
```

---

## 14. Body Equilibrium (Forces sum to zero)
التأكد من أن الجسم متزن بناءً على مجموع متجهات القوى.

```cpp
#include <iostream>
using namespace std;
int main ()
{
    int n ;
    int SumZ=0;
    int SumY=0;
    int SumX=0;
    cin >> n;
    int x , y , z;
    for (int i = 0; i < n ; i++)
    {
        cin >> x >> y >> z;
        SumX +=x;
        SumY +=y;
        SumZ +=z;
    }
    if ( SumX == 0 &&  SumY == 0 && SumZ == 0 )
    {
        cout << "YES";
    }
    else 
    {
        cout << "NO";
    }
    return 0;
}
```

---

## 15. Nearly Lucky Number
التحقق مما إذا كان عدد الأرقام المحظوظة (4 أو 7) في رقم ما هو نفسه رقم محظوظ.

```cpp
#include <iostream>
#include <string>
using namespace std; 
int main ()
{   
    int luckyCount=0;
    string S;
    cin >> S;
    for (size_t i = 0; i < S.length();i++)
    {
        if(S[i] ==  '4' || S[i] == '7'){
            luckyCount++;
        }
    }
    bool isLucky = true;
    if (luckyCount == 0){
        isLucky = false;
    }
    while(luckyCount > 0) {
        int digit = luckyCount % 10;
        if (digit != 4 && digit != 7){
            isLucky= false;
        }
        luckyCount /= 10;
    }
    if (isLucky){
        cout << "YES";
    }
    else 
    {
        cout << "NO";
    }
}
```

---

## 16. Anton and Danik
تحديد من فاز أكثر في مباريات الشطرنج بين أنطون ودانيك.

```cpp
#include <iostream>
#include <string>
using namespace std;
int main ()
{
    int n;
    int countA = 0;
    int countD = 0;
    string S;
    cin >> n >> S;
    for (size_t i = 0; i < S.length();i++)
    {
        char c = S[i];
        if (c == 'A')
        {
            countA++;
        }
        else if (c == 'D')
        {
            countD++;
        }
    }
    if (countA > countD)
    {
        cout << "Anton";
    }
    else if (countD > countA)
    {
        cout << "Danik";
    }
    else 
    {
        cout << "Friendship";
    }
}
```

---

## 17. Football Dangerous Situation
التحقق من وجود 7 لاعبين متتاليين من نفس الفريق (خطر).

```cpp
#include <iostream>
#include <string>
using namespace std;
int main ()
{
    int count = 1;
    string S;
    cin >> S;
    for(size_t i = 1; i < S.length();i++)
    {
        if (S[i] == S[i-1] )
        {
            count++;
            if (count >= 7)
            {
                cout << "YES";
                return 0;
            }
        }
        else {
            count = 1;
        }
    }
    cout << "NO";
    return 0;
}
```

---

## 18. Berland and Birland Reversed Word
التحقق من أن كلمة t هي عكس الكلمة s.

```cpp
#include <iostream>
#include <string>
#include <algorithm>
using namespace std;
int main ()
{
    string s,t;
    cin >> s >> t;
    reverse(s.begin(),s.end());
    if(s == t)
    {
        cout << "YES";
    }
    else 
    {
        cout << "NO";
    }
    return 0;
}
```

---

## 19. Vanya and Fence
حساب عرض الطريق اللازم بحيث لا يلاحظ الحارس أي شخص طوله أكبر من ارتفاع السور.

```cpp
#include <iostream>
using namespace std;
int main ()
{
    int n , h ;
    int totalWidth = 0;
    cin >> n >> h;
    for (int i = 0; i < n;i++)
    {
        int a;
        cin >> a;
        if (a <= h)
            totalWidth++;
        else 
            totalWidth += 2;
    }
    cout << totalWidth;
}
```

---

## 20. Tram (Minimum Capacity)
حساب أقل سعة يجب أن يمتلكها الترام بناءً على صعود ونزول الركاب في كل محطة.

```cpp
#include <iostream>
#include <algorithm>
using namespace std;
int main ()
{
    int n ;
    int maxCapacity = 0;
    int currentPassenger = 0;
    cin >> n;
    for(size_t i = 0; i < n; i++)
    {
        int a , b ;
        cin >> a >> b;
        currentPassenger -= a;
        currentPassenger += b;
        maxCapacity = max(maxCapacity , currentPassenger);
    }
    cout << maxCapacity;
}
```

---

## 21. Easy Problem
التحقق مما إذا كانت المسألة سهلة (لا يوجد رأي "صعب") أو صعبة.

```cpp
#include <iostream>
using namespace std;
int main ()
{
    int n; 
    cin >> n ;
    for(size_t i = 0; i < n ; i++)
    {
        int k;
        cin >> k;
        if (k == 1){
            cout << "HARD";
            return 0;
        }
    }
    cout << "EASY";
}
```

---


## 22. Queue at the School
محاكاة التغييرات في مصفوفة/نص خطوة بخطوة عبر الزمن (Simulation)

```cpp
#include <iostream>
#include <algorithm>
#include <string>
using namespace std;

int main() {
    
    ios_base::sync_with_stdio(false);
    cin.tie(NULL);

    int n, t;
    cin >> n >> t;

    string S;
    cin >> S;

    
    while (t--) {
        for (size_t i = 0; i < n - 1; i++) {
           
            if (S[i] == 'B' && S[i + 1] == 'G') {
                swap(S[i], S[i + 1]);
                i++; 
            }
        }
    }

    cout << S << endl; ```
---
## 23. George and Alex (Codeforces 467A)

حساب عدد الغرف المتاحة لشخصين بناءً على السعة الكلية وعدد السكان الحاليين.
```cpp
#include <iostream>

using namespace std;

int main() {
    // Fast I/O
    ios_base::sync_with_stdio(false);
    cin.tie(NULL);

    int n;
    cin >> n; // Number of rooms

    int count = 0; // Counter for suitable rooms

    for (int i = 0; i < n; i++) {
        int p, q;
        cin >> p >> q; // p = current occupants, q = total capacity

        // Check if there is enough space for 2 people
        if (q - p >= 2) {
            count++;
        }
    }

    cout << count << "\n";

    return 0;
}
