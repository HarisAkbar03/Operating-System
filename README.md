#include<stdio.h>
#include<pthread.h>
#include<iostream>
#include<unistd.h>
using namespace std;
 
int main()
{
    int arr[20];
    for (int i = 0; i < 20; i++)
    {
        arr[i] = rand() % 100;
    }
    cout<<"The Contents of Array are = ";
    for (int i = 0; i < 20; i++)
    {
        cout<< arr[i] << " , ";
    }
    cout<<endl;
    pid_t c_pid = fork();

    if(c_pid < 0 )
    {
        cout<<"Fork Failed"<<endl;
    }
    if(c_pid == 0 )
    {
        int min = arr[9];
        for (int i = 10; i < 20; i++)
        {
            if(arr[i] < min)
            {
                min = arr[i];
            }
            
        }
        cout << "The minimum value in the array is: " << min << endl;
        cout<<"Child Process id is "<<getpid()<<endl;
        
    }
    else
    {
        int min = arr[0];
        for (int i = 1; i < 10; i++)
        {
            if(arr[i] < min)
            {
                min = arr[i];
            }
            
        }
        cout << "The minimum value in the array is: " << min << endl;
        cout<<"Parent Process id is "<<getpid()<<endl;
    }
}
