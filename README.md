bai 1
#include <iostream>
using namespace std;
typedef struct hang_cot_va_ten
{
    int hang;
    int cot;
    char ten[20];
}hct;

istream& operator >> (istream& is, hct& a)
{
    cout << "nhap ten mt: ";
    is >> a.ten;
    cout << "\nnhap hang va cot: ";
    is >> a.hang >> a.cot; cout << "\n";
    return is;
}

typedef int MT[20][20];

void nhapmt(MT a, char* ten, int m, int n)
{
    for (int i = 0; i < m; i++)
    {
        for (int j = 0; j < n; j++)
        {
            cout << "nhap phan tu " << i << " " << j << " " << "cua " << ten << ": ";
            cin >> a[i][j];
        }
    }
}

void inmt (MT a, char* ten, int m, int n)
{
    cout << "ma tran " << ten << " co dang: " << endl;
    for (int i = 0; i < m; i++)
    {
        for (int j = 0; j <= n; j++)
        {
            if (j == n)
            {
                cout << "\n";
                break;
            }
            cout << a[i][j] << " ";
        }
    }
}

void nhapmt(MT a, char* ten, int n)
{
    for (int i = 0; i < n; i++)
    {
        for (int j = 0; j < n; j++)
        {
            cout << "nhap phan tu " << i << " " << j << ": ";
            cin >> a[i][j];
        }
    }
}

void inmt (MT a, char* ten, int n)
{
    cout << "ma tran " << ten << " co dang: " << endl;
    for (int i = 0; i < n; i++)
    {
        for (int j = 0; j <= n; j++)
        {
            if (j == n)
            {
                cout << "\n";
                break;
            }
            cout << a[i][j] << " ";
        }
    }
}

void nhanmt (MT a, MT b, MT c, int m, int n, int p)
{
    int d = 0;
    for (int i = 0; i < m; i++)
    {
        for (int j = 0; j < p; j++)
        {
            for (int k = 0; k < n; k++)
            {
                d = d + a[i][k] * b[k][j];
                c[i][j] = d;
            }
            d = 0;
        }
    }
}

void nhanmt (MT a, MT b, MT c, int n)
{
    int d = 0;
    for (int i = 0; i < n; i++)
    {
        for (int j = 0; j < n; j++)
        {
            for (int k = 0; k < n; k++)
            {
                d = d + a[i][k] * b[k][j];
                c[i][j] = d;
            }
            d = 0;
        }
    }
}

int main()
{
    MT A, B, C, D, E, F;
    hct a, b, c, d, e, f;
    cin >> a; nhapmt(A, a.ten, a.hang, a.cot); inmt(A, a.ten, a.hang, a.cot);
    cin >> b; nhapmt(B, b.ten, b.hang, b.cot); inmt(B, b.ten, b.hang, b.cot);
    cin >> c; nhapmt(C, c.ten, c.hang); inmt(C, c.ten, c.hang);
    cin >> d; nhapmt(D, d.ten, d.hang); inmt(D, d.ten, d.hang); fflush(stdin);
    nhanmt(A, B, E, a.hang, a.cot, b.cot);
    cout << "dat ten mt tich cua " << a.ten << " va " << b.ten << " : "; gets(e.ten);
    inmt(E, e.ten, a.hang, b.cot);
    nhanmt(C, D, F, c.hang);
    cout << "dat ten mt tich cua " << c.ten << " va " << d.ten << " : "; gets(f.ten);
    inmt(F, f.ten, c.hang);
}
bai 2
#include <iostream>
#include <math.h>
using namespace std;
typedef struct
{
    int a, b;
}PS;

ostream& operator << (ostream& os, PS& p)
{
    os << p.a << "/" << p.b;
    return os;
}

istream& operator >> (istream& is, PS& p)
{
    cout<<"Tu va Mau: ";
    is >> p.a >> p.b;
    return is;
}

int uscln(int x, int y)
{
    x = abs(x); y = abs(y);
    int n; int uscln = 1;
    if (x > y)
    {
        n = y;
    }else
    {
        n = x;
    }
    for (int i = 1; i <= n; i++)
    {
        if (x % i == 0 && y % i == 0)
        {
            uscln = i;
        }
    }
    return uscln;
}

PS operator * (PS p1, PS p2)
{
    PS psm;
    psm.a = p1.a * p2.a;
    psm.b = p1.b * p2.b;
    return psm;
}

PS operator + (PS p1, PS p2)
{
    PS psm, p1m, p2m;
    if (p1.b == p2.b)
    {
        psm.a = p1.a + p2.a;
        psm.b = p1.b;
    }else if (p1.b != p2.b)
    {
        p1m.a = p1.a * p2.b;
        p2m.a = p2.a * p1.b;
        p1m.b = p1.b * p2.b;
        p2m.b = p1.b * p2.b;
        psm.a = p1m.a + p2m.a;
        psm.b = p1m.b;
    }
    return psm;
}

PS operator - (PS p1, PS p2)
{
    PS psm, p1m, p2m;
    if (p1.b == p2.b)
    {
        psm.a = p1.a - p2.a;
        psm.b = p1.b;
    }else if (p1.b != p2.b)
    {
        p1m.a = p1.a * p2.b;
        p2m.a = p2.a * p1.b;
        p1m.b = p1.b * p2.b;
        p2m.b = p1.b * p2.b;
        psm.a = p1m.a - p2m.a;
        psm.b = p1m.b;
    }
    return psm;
}

PS operator / (PS p1, PS p2)
{
    PS psm;
    psm.a = p1.a * p2.b;
    psm.b = p1.b * p2.a;
    return psm;
}

PS rutgon (PS p)
{
    int sc = uscln(p.a, p.b);
    p.a = (p.a) / sc;
    p.b = (p.b) / sc;
    return p;
}

int main()
{
    PS p, q, z, u, v;
    PS s;
    cout << "Nhap cac phan so p, q, z, u, v\n";
    cin >> p >> q >> z >> u >> v;
    s = rutgon((p - q * z) / (u + v));
    cout << "Phan so s = " << s << endl;
}
    
