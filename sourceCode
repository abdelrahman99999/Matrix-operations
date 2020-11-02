#include <vector>
#include<string>
#include <iostream>
#include<sstream>
#include<cstdlib>
using namespace std;
/*********************************************************************************************************************************
*												FUNCTIONS DECLARATION															 *
*********************************************************************************************************************************/
vector<vector<double>>matrix_f_string(int x, string y);
void getCofactor(vector<vector<double>>A, vector<vector<double>>&sum, int p, int q, int n);
float determinant(vector<vector<double>> A, int N);
void adjoint(vector<vector<double>> A, vector<vector<double>> &adj, int N);
bool inverse(vector<vector<double>> A, vector<vector<double>> &inverse, int N);
void transpose(vector<vector<double>>y, int x);
void add(vector<vector<double>>x, vector<vector<double>>y, vector<vector<double>>&sum, int no);
void substract(vector<vector<double>>x, vector<vector<double>>y, vector<vector<double>>&sum, int no);
void multiblication(vector<vector<double>>x, vector<vector<double>>y, vector<vector<double>>&sum, int no);
void division(vector<vector<double>>x, vector<vector<double>>y, vector<vector<double>>&sum, int no);
void print_matrix(vector< vector<double> >matrix);
void f(vector<vector<double>> arr1, vector<vector<double>> arr2, vector<vector<double>>&sum, string s1, int x);
//FOR MORE ONE OPERATION
void f2(vector<vector<double>> arr1, vector<vector<double>> arr2, vector<vector<double>>&sum, string s1, int x, int in);
void f_for_more2(vector<vector<vector<double>>> arr, string s1, int x, int counter);
/*********************************************************************************************************************************
*												MAIN FUNCTION																	 *
*********************************************************************************************************************************/
int main() {
	int i, j;
	string s;
	int x; string y;    // x IS THE SIZE OF MATRIX
	cout << "enter n which n*n is the size of matrices  \n";
	cin >> x;
	vector<vector<vector<double>>> arr(50, vector<vector<double>>(x, vector<double>(x))); // 3D VECTOR TO STORE MATRICES INSIDE IT AND CALLING IT BY INDEX
	static int counter = 0;              //counter >> A WAY TO COUNT THE NUMBERS OF THE MATRICES ENTERED
	do {
		cin.ignore();
		cout << "enter the matrix as formula \"A =[1 2; 3 4] \"if n=2 or \"B =[1 2 3; 4 5 6; 7 8 9]\" if n=3...etc \n";
		getline(cin, y);                 // RECEPTION THE MATRIX AS STRING
		vector< vector<double> >pp;
		pp = matrix_f_string(x, y);		//FUNCTION USED TO EXTRACT THE NUMBERS FROM THE STRING AND STORE THE VALUES IN VECTOR pp
		for (i = 0; i < x; i++) {
			for (j = 0; j < x; j++)
				arr[counter][i][j] = pp[i][j];
		}
		cout << "do you want to add another matrix ( yes / no ) ??   \t if you write no,click 2 enter \n";
		cin >> s;
		counter++;
	} while (s == "yes" || s == "YES");
	cin.ignore();
	string s1;

	do {
		vector<vector<double>>sum(x, vector<double>(x));
		cin.ignore();
		// counter EQUAL THE NUMBERS OF THE MATRICES
		if (counter == 1) {
			cout << "write an experasion to do operation \n";
			cout << "to Show Matrix elements , write:  A \n";
			cout << "to do Transpose ,write: C = A' \n";
			cout << "to get determinant of matrix , write: det of A\n";
			cout << " to show the inverse of matrix,write: A-1\n";
			getline(cin, s1);
			//show
			if (s1.size() == 1) {
				print_matrix(arr.at(0));

			}
			//transpose
			if (s1.size() == 6) {
				transpose(arr.at(0), x);
			}
			//determinant
			if (s1.size() == 8) {
				cout << "-----------------------\n";
				cout << determinant(arr.at(0), x) << endl;
			}
			//inverse
			if (s1.size() == 3) {
				if (inverse(arr.at(0), sum, x)) {
					print_matrix(sum);
				}
			}
		}
		if (counter == 2) {
			cout << "write an exprasion to do operation \t \t \t\tNOTE: A is the 1st matrix , B is 2th matrix\n";
			cout << "to Show Matrix elements : write  A  or B \n";
			cout << "to get determinant of matrix : write det of A or det of B \n";
			cout << "to do Addition : write C = A + B                \t \tyou must write expration with spaces and upper letters\n";
			cout << "to do Subtraction :write C = A - B  or C = B - A\n";
			cout << "to do Multiplication :write  C = A * B or C = B * A\n";
			cout << "to do Transpose :write C = A' or C = B' \n";
			cout << "to do Division :write C = A / B or C = B / A\n";
			getline(cin, s1);
			//DETERMINANT
			if (s1.size() == 8) {
				if (s1[7] == 'A') {
					cout << "-----------------\n";
					cout << determinant(arr.at(0), x) << endl;
				}
				if (s1[7] == 'B') {
					cout << "-----------------\n";
					cout << determinant(arr.at(1), x) << endl;
				}
			}
			//Addition  //Subtraction //Multiplication //Division
			f(arr.at(0), arr.at(1), sum, s1, x);
			//SHOWING ELEMENTS
			if (s1.size() == 1) {
				if (s1.at(0) == 'A' || s1.at(0) == 'a') {
					print_matrix(arr.at(0));
				}
				if (s1.at(0) == 'B' || s1.at(0) == 'b') {
					print_matrix(arr.at(1));
				}
			}
			//transpose
			if (s1.size() == 6) {
				if (s1.at(4) == 'A' || s1.at(4) == 'a') {
					transpose(arr.at(0), x);
				}
				if (s1.at(4) == 'B' || s1.at(4) == 'b') {
					transpose(arr.at(1), x);
				}
			}
		}
		if (counter >= 3)
		{
			cout << "you must use the matrices as you entered in order\n ";
			cout << "you will write as you calculate numbers A * B - C + D / e ....etc (put space between any two char)\n";
			getline(cin, s1);
			f_for_more2(arr, s1, x, counter); // FUNCTION USED TO DO OPERATION AMONG MORE THAN TWO MATRICES  (+ , - , * , /)
		}
		cout << "if you want another operation for the matrices you entered write continue/CONTINUE \n";
		cout << "if you want to end the program write exit/EXIT  \n";
		string u;
		cin >> y;
	} while (y == "continue" || y == "CONTINUE");
	cout << "-_- -_- -_- -_- -_- -_- -_- -_- -_- -_- -_- -_-\n";
	cout << "thank you \n";

	cout << endl;
	return 0;
}
/********************************************************************************************************************************
*												FUNCTIONS DEFINATION															*
********************************************************************************************************************************/
vector<vector<double>>matrix_f_string(int x, string y)
{
	stringstream ss(y);
	vector<vector<double>>matrix;
	vector<double>temp;
	char a;
	double p;
	ss >> a >> a >> a;
	for (int i = 0; i < x; i++)
	{
		for (int j = 0; j < x; j++)
		{
			ss >> p;
			temp.push_back(p);
		}
		ss >> a;
		matrix.push_back(temp);
		for (int j = 0; j < x; j++)
			temp.pop_back();
	}
	return matrix;
}
void getCofactor(vector<vector<double>>A, vector<vector<double>>&sum, int p, int q, int n)
{
	int i = 0, j = 0;
	for (int row = 0; row < n; row++)
	{
		for (int col = 0; col < n; col++)
		{
			if (row != p && col != q)
			{
				sum[i][j++] = A[row][col];
				if (j == n - 1)
				{
					j = 0;
					i++;
				}
			}
		}
	}
}
float determinant(vector<vector<double>> A, int N)
{
	double D = 0; // Initialize result 

				  // Base case : if matrix contains single element 
	if (N == 1)
		return A[0][0];

	vector<vector<double>> sum(N, vector<double>(N)); // To store cofactors 

	float sign = 1; // To store sign multiplier 

					// Iterate for each element of first row 
	for (int f = 0; f < N; f++)
	{
		// Getting Cofactor of A[0][f] 
		getCofactor(A, sum, 0, f, N);
		D += sign * A[0][f] * determinant(sum, N - 1);

		// terms are to be added with alternate sign 
		sign = -sign;
	}

	return D;
}
void adjoint(vector<vector<double>> A, vector<vector<double>> &adj, int N)
{
	if (N == 1)
	{
		adj[0][0] = 1;
		return;
	}
	float sign = 1;
	vector<vector<double>> temp(N, vector<double>(N));

	for (int i = 0; i<N; i++)
	{
		for (int j = 0; j<N; j++)
		{
			getCofactor(A, temp, i, j, N);
			sign = ((i + j) % 2 == 0) ? 1 : -1;
			adj[j][i] = (sign)*(determinant(temp, N - 1));
		}
	}
}
bool inverse(vector<vector<double>> A, vector<vector<double>> &inverse, int N)
{
	double det = determinant(A, N);
	if (det == 0)
	{
		cout << "Singular matrix, can't find its inverse\n";
		return false;
	}
	vector<vector<double>> adj(N, vector<double>(N));
	adjoint(A, adj, N);
	for (int i = 0; i<N; i++)
		for (int j = 0; j<N; j++)
			inverse[i][j] = adj[i][j] / (det);

	return true;
}
void transpose(vector<vector<double>>y, int x)
{
	cout << "----------------------- \n";
	for (int i = 0; i < x; i++) {
		for (int j = 0; j < x; j++)
			cout << y[j][i] << " ";
		cout << endl;
	}
}
void add(vector<vector<double>>x, vector<vector<double>>y, vector<vector<double>>&sum, int no)
{

	for (int i = 0; i < no; i++) {
		for (int j = 0; j < no; j++)
			sum[i][j] = x[i][j] + y[i][j];
	}
}
void substract(vector<vector<double>>x, vector<vector<double>>y, vector<vector<double>>&sum, int no)
{
	for (int i = 0; i < no; i++) {
		for (int j = 0; j < no; j++)
			sum[i][j] = x[i][j] - y[i][j];
	}
}
void multiblication(vector<vector<double>>x, vector<vector<double>>y, vector<vector<double>>&sum, int no)
{
	for (int i = 0; i < no; ++i)
		for (int j = 0; j < no; ++j)
			for (int k = 0; k < no; ++k)
				sum[i][j] += x[i][k] * y[k][j];

}
void division(vector<vector<double>>x, vector<vector<double>>y, vector<vector<double>>&sum, int no) {
	vector<vector<double>>inv(no, vector<double>(no));
	inverse(y, inv, no);
	multiblication(x, inv, sum, no);
}
void print_matrix(vector< vector<double> >matrix)
{
	cout << "----------------------- \n";
	for (int i = 0; i < matrix.size(); i++) {
		for (int j = 0; j < matrix.size(); j++)
			cout << matrix[i][j] << " ";
		cout << endl;
	}
}
void f(vector<vector<double>> arr1, vector<vector<double>> arr2, vector<vector<double>>&sum, string s1, int x)
{

	if (s1.size() == 9)       //Addition  //Subtraction //Multiplication //Division
	{
		if (s1[6] == '+')
		{
			add(arr1, arr2, sum, x);
			print_matrix(sum);
		}
		if (s1[6] == '-') {
			if (s1[4] == 'A') {
				substract(arr1, arr2, sum, x);
				print_matrix(sum);
			}
			if (s1[4] == 'B') {
				substract(arr2, arr1, sum, x);
				print_matrix(sum);
			}
		}
		if (s1[6] == '*') {
			if (s1[4] == 'A') {
				multiblication(arr1, arr2, sum, x);
				print_matrix(sum);
			}
			if (s1[4] == 'B') {
				multiblication(arr2, arr1, sum, x);
				print_matrix(sum);
			}
		}
		if (s1[6] == '/') {
			if (s1[4] == 'A') {
				division(arr1, arr2, sum, x);
				if (determinant(arr2, x) != 0) {
					print_matrix(sum);
				}
			}
			if (s1[4] == 'B') {
				division(arr2, arr1, sum, x);
				if (determinant(arr1, x) != 0) {
					print_matrix(sum);
				}
			}
		}
	}

	cout << endl;
}
//FOR MORE ONE OPERATION
void f2(vector<vector<double>> arr1, vector<vector<double>> arr2, vector<vector<double>>&sum, string s1, int x, int in)
{
	if (s1[in] == '*')
	{
		multiblication(arr1, arr2, sum, x);
	}
	if (s1[in] == '/')
	{
		division(arr1, arr2, sum, x);
		if (determinant(arr2, x) == 0) {
			cout << " result is the result of operations after  illegel division  \n";
			cout << "if the illegal division is the  last operation ,the result equal zero\n";
		}
	}
	if (s1[in] == '+')
	{
		add(arr1, arr2, sum, x);
	}
	if (s1[in] == '-')
	{
		substract(arr1, arr2, sum, x);
	}

}
void f_for_more2(vector<vector<vector<double>>> arr, string s1, int x, int counter)
{
	vector<vector<vector<double>>> result(11, vector<vector<double>>(x, vector<double>(x)));
	vector<vector<double>>su(x, vector<double>(x));
	if (counter == 3)
	{
		f2(arr[0], arr[1], result[0], s1, x, 2);
		f2(result[0], arr[2], su, s1, x, 6);
		print_matrix(su);
	}
	if (counter == 4)
	{
		f2(arr[0], arr[1], result[0], s1, x, 2);
		f2(result[0], arr[2], result[1], s1, x, 6);
		f2(result[1], arr[3], su, s1, x, 10);
		print_matrix(su);
	}
	if (counter == 5)
	{
		f2(arr[0], arr[1], result[0], s1, x, 2);
		f2(result[0], arr[2], result[1], s1, x, 6);
		f2(result[1], arr[3], result[2], s1, x, 10);
		f2(result[2], arr[4], su, s1, x, 14);
		print_matrix(su);
	}
	if (counter == 6)
	{
		f2(arr[0], arr[1], result[0], s1, x, 2);
		f2(result[0], arr[2], result[1], s1, x, 6);
		f2(result[1], arr[3], result[2], s1, x, 10);
		f2(result[2], arr[4], result[3], s1, x, 14);
		f2(result[3], arr[5], su, s1, x, 18);
		print_matrix(su);
	}
	if (counter == 7) {
		f2(arr[0], arr[1], result[0], s1, x, 2);
		f2(result[0], arr[2], su, s1, x, 6);
		f2(result[1], arr[3], result[2], s1, x, 10);
		f2(result[2], arr[4], result[3], s1, x, 14);
		f2(result[3], arr[5], result[4], s1, x, 18);
		f2(result[4], arr[6], su, s1, x, 22);
		print_matrix(su);
	}
	if (counter == 8) {
		f2(arr[0], arr[1], result[0], s1, x, 2);
		f2(result[0], arr[2], su, s1, x, 6);
		f2(result[1], arr[3], result[2], s1, x, 10);
		f2(result[2], arr[4], result[3], s1, x, 14);
		f2(result[3], arr[5], result[4], s1, x, 18);
		f2(result[4], arr[6], result[5], s1, x, 22);
		f2(result[5], arr[7], su, s1, x, 26);
		print_matrix(su);
	}
	if (counter == 9) {
		f2(arr[0], arr[1], result[0], s1, x, 2);
		f2(result[0], arr[2], su, s1, x, 6);
		f2(result[1], arr[3], result[2], s1, x, 10);
		f2(result[2], arr[4], result[3], s1, x, 14);
		f2(result[3], arr[5], result[4], s1, x, 18);
		f2(result[4], arr[6], result[5], s1, x, 22);
		f2(result[5], arr[7], result[6], s1, x, 26);
		f2(result[6], arr[8], su, s1, x, 30);
		print_matrix(su);
	}
	if (counter == 10) {
		f2(arr[0], arr[1], result[0], s1, x, 2);
		f2(result[0], arr[2], su, s1, x, 6);
		f2(result[1], arr[3], result[2], s1, x, 10);
		f2(result[2], arr[4], result[3], s1, x, 14);
		f2(result[3], arr[5], result[4], s1, x, 18);
		f2(result[4], arr[6], result[5], s1, x, 22);
		f2(result[5], arr[7], result[6], s1, x, 26);
		f2(result[6], arr[8], result[7], s1, x, 30);
		f2(result[7], arr[9], su, s1, x, 34);
		print_matrix(su);
	}
}
/********************************************************************************************************************************
*													END OF THE PROGRAM															*
********************************************************************************************************************************/
