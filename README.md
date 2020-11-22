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
