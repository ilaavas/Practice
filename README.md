#include<iostream>
#include<cmath>
using namespace std;

class shape
{
 protected:
  float area, perimeter;
 public:
  shape(){}
  virtual void initialise()=0;
  virtual float computeArea()=0;
  virtual float computePeri()=0;
  virtual ~shape(){cout<<"Destructor";}
};

class triangle:public shape
{
 float p,q,r;
 void initialise()
 {
  cout<<"Enter the three sides:";
  cin>>p>>q>>r;
 }
 float computeArea()
 {
  float x=computePeri();
  float s=x/2;
  area=sqrt(s*(s-p)*(s-q)*(s-r));
  return area;
 }
 float computePeri()
 {
  perimeter=p+q+r;
  return perimeter;
 }
};

class rectangle:public shape
{
 float l,b;
 void initialise()
 {
   cout<<"Enter length and breadth:";
  cin>>l>>b;
 }
 float computeArea()
 {
  float area=l*b;
  return area;
 }
 float computePeri()
 {
  perimeter=2*(l+b);
  return perimeter;
 }
};

int main()
{
 shape *base;
 triangle ob1;
 rectangle ob2;
 base=&ob1;
 base->initialise();
 cout<<"Area of triangle: "<<base->computeArea()<<endl;
 cout<<"Peri of triangle is: "<<base->computePeri()<<endl;
 base=&ob2;
 base->initialise();
 cout<<"Area of rectangle: "<<base->computeArea()<<endl;
 cout<<"Peri of rectangle: "<<base->computePeri()<<endl;
 return 0;
}
