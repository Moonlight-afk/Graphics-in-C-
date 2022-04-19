#include <graphics.h>
#include <iostream>
#include "math.h"
#include <conio.h>
#include <vector>

using namespace std;

vector<float> vector1(3);
vector<float> vector2(3);
vector<float> rec1(3);
vector<float> rec2(3);
float newZ[3][3];
float dubZ[3][3];
vector<float> out1(3);
vector<float> out2(3);
float lenX;
float lenY;
float ku;

//koordinatnaya ploskost'
void koordinat(){
    int maxx = getmaxx();
    int maxy = getmaxy();
    maxx += 1;
    maxy +=1;
	line(0, maxy/2, maxx, maxy/2);
	line(maxx/2, 0, maxx/2 ,maxy);
}

/*void newline(vector<float>& vector1,vector<float>& vector2){
    int maxx = getmaxx();
    int maxy = getmaxy();
    int x1,y1,x2,y2;
    maxx += 1;
    maxy +=1;
    x1 = vector1[0];
    y1 = vector1[1];
    x2 = vector2[0];
    y2 = vector2[1];
    cout<<"Newline\n";
    cout<<vector1[0]<<" "<<vector1[1]<<" "<<vector1[2]<<"\n";
    cout<<vector2[0]<<" "<<vector2[1]<<" "<<vector2[2]<<"\n";
    line(vector1[0]+(maxx/2),(vector1[1]*-1)+(maxy/2),vector2[0]+(maxx/2),(vector2[1]*-1)+(maxy/2));
}*/

void umnoz(float newZ[3][3],float Matrix1[3][3],float Matrix2[3][3]){

    for(int i=0;i<3;i++){
        for(int j=0;j<3;j++){
            for(int k=0;k<3;k++){
                newZ[i][j] += Matrix1[i][k]*Matrix2[k][j];
            }
        }
    }

}
void simetri(vector<float> vector1, vector<float> vector2, int x, int y){
    float Oy1;
    float Oy2;
    float Ox1;
    float Ox2;

    Ox1=(x/2)-vector1[0];
    Ox2=(x/2)-vector2[0];
    Oy1=(y/2)-vector1[1];
    Oy2=(y/2)-vector2[1];

    line(Ox1,Oy1,Ox2,Oy2);


}

void mashtab(float mnoz,vector<float> &vector1,vector<float> &vector2,float Scaling[3][3],float Shift[3][3],float& x1,float& y1,float& x2,float& y2){


    Scaling[0][0] = mnoz;
    Scaling[1][1] = mnoz;

    for(int i=0;i<3;i++){
        for(int j=0;j<3;j++){
            newZ[i][j]=0.0;
        }
    }

    Shift[2][0] = -lenX;
    Shift[2][1] = -lenY;

    umnoz(newZ,Shift,Scaling);
    for(int i=0;i<3;i++){
        for(int j=0;j<3;j++){
            dubZ[i][j]=newZ[i][j];
        }
    }
    Shift[2][0] = lenX;
    Shift[2][1] = lenY;

    for(int i=0;i<3;i++){
        for(int j=0;j<3;j++){
            newZ[i][j]=0.0;
        }
    }

    umnoz(newZ,dubZ,Shift);


    for(int i=0;i<3;i++){
        out1[i]=0;
        out2[i]=0;
        for(int j=0;j<3;j++){
            out1[i] += vector1[j]*newZ[j][i];
            out2[i] += vector2[j]*newZ[j][i];
        }
    }

    vector1[0]=out1[0];
    vector1[1]=out1[1];
    vector2[0]=out2[0];
    vector2[1]=out2[1];
    x1 = vector1[0];
    y1 = vector1[1];
    x2 = vector2[0];
    y2 = vector2[1];

}

void turned(int ku,vector<float> &vector1,vector<float> &vector2,float Turn[3][3],float Scaling[3][3],float x1,float y1,float x2, float y2,float Shift[3][3]){
    Turn[0][0] = cos((ku*3.14)/180);
    Turn[0][1] = sin((ku*3.14)/180);
    Turn[1][0] = -sin((ku*3.14)/180);
    Turn[1][1] = cos((ku*3.14)/180);
    Turn[2][2] = 1.0;


    /*float dubX2;
    float dubY2;
    dubX2=vector2[0];
    dubY2=vector2[1];

    vector2[0] = vector1[0] + (dubX2-vector1[0])*Turn[0][0] + (dubY2-vector1[1])*Turn[0][1];
    vector2[1] = vector1[1] + (dubX2-vector1[0])*Turn[1][0] + (dubY2-vector1[1])*Turn[1][1];

    vector2[0]=round(vector2[0]);
    vector2[1]=round(vector2[1]);*/
    for(int i=0;i<3;i++){
        for(int j=0;j<3;j++){
            newZ[i][j]=0.0;
        }
    }

    Shift[2][0] = -lenX;
    Shift[2][1] = -lenY;

    umnoz(newZ,Shift,Turn);
    for(int i=0;i<3;i++){
        for(int j=0;j<3;j++){
            dubZ[i][j]=newZ[i][j];
        }
    }
    Shift[2][0] = lenX;
    Shift[2][1] = lenY;

    for(int i=0;i<3;i++){
        for(int j=0;j<3;j++){
            newZ[i][j]=0.0;
        }
    }

    umnoz(newZ,dubZ,Shift);


    for(int i=0;i<3;i++){
        out1[i]=0;
        out2[i]=0;
        for(int j=0;j<3;j++){
            out1[i] += vector1[j]*newZ[j][i];
            out2[i] += vector2[j]*newZ[j][i];
        }
    }

    vector1[0]=out1[0];
    vector1[1]=out1[1];
    vector2[0]=out2[0];
    vector2[1]=out2[1];
    x1 = vector1[0];
    y1 = vector1[1];
    x2 = vector2[0];
    y2 = vector2[1];


}



void move(vector<float>& vector1,vector<float>& vector2, float matricsdvig[3][3],float x1,float y1,float x2,float y2,float Scaling[3][3],float Turn[3][3]){
    int maxx = getmaxx();
    int maxy = getmaxy();
    maxx += 1;
    maxy +=1;
    std::cout<<"Hto sdelat?\n";
    std::cout<<"1. Up(w)\n";
    std::cout<<"2. Down(s)\n";
    std::cout<<"3. Right(d)\n";
    std::cout<<"4. Left(a)\n";
    std::cout<<"5. Bolhe(e)\n";
    std::cout<<"6. Menhe(q)\n";
    std::cout<<"7. Simmetriya(f)\n";
    std::cout<<"8. Povorot(z)\n";
    std::cout<<"9. Povorot v druguy(x)\n";
    lenX=(abs(vector1[0])+abs(vector2[0]))/2;
    lenY=(abs(vector1[1])+abs(vector2[1]))/2;
    char a;
    while (a!='o'){
        a = _getch();
        float mnoz;
        float Shift[3][3];
        for(int i=0;i<3;i++){
            for(int j=0;j<3;j++){
                if(i==j){
                    Shift[i][j]=1.0;
                }
                else
                    Shift[i][j]=0.0;
            }
        }
        switch(a){
        case 'w':
            rec1[0] = 0;
            rec1[1] = 0;
            rec1[2] = 0;
            for(int i=0;i<3;i++){
                rec1[i] = 0;
                for(int j=0;j<3;j++){
                    rec1[i] += matricsdvig[j][i] * vector1[j];
                }
            }
            rec2[0] = 0;
            rec2[1] = 0;
            rec2[2] = 0;
            for(int i=0;i<3;i++){
                rec2[i] = 0;
                for(int j=0;j<3;j++){
                    rec2[i] += matricsdvig[j][i] * vector2[j];
                }
            }
            vector1[1] = rec1[1];
            vector2[1] = rec2[1];
            rec1[0] = vector1[0];
            rec2[0] = vector2[0];
            clearviewport();
            koordinat();
            line(vector1[0]+(maxx/2),(rec1[1]*-1)+(maxy/2),vector2[0]+(maxx/2),(rec2[1]*-1)+(maxy/2));
            y1 = vector1[1];
            y2 = vector2[1];
            break;
        case 's':
            rec1[0] = 0;
            rec1[1] = 0;
            rec1[2] = 0;
            for(int i=0;i<3;i++){
                rec1[i] = 0;
                for(int j=0;j<3;j++){
                    rec1[i] += matricsdvig[j][i] * vector1[j];
                }
            }
            rec1[1] -= matricsdvig[2][0] * 2;
            rec2[0] = 0;
            rec2[1] = 0;
            rec2[2] = 0;
            for(int i=0;i<3;i++){
                rec2[i] = 0;
                for(int j=0;j<3;j++){
                    rec2[i] += matricsdvig[j][i] * vector2[j];
                }
            }
            rec2[1] -= matricsdvig[2][0] * 2;
            vector1[1] = rec1[1];
            vector2[1] = rec2[1];
            rec1[0] = vector1[0];
            rec2[0] = vector2[0];
            clearviewport();
            koordinat();
            line(vector1[0]+(maxx/2),(rec1[1]*-1)+(maxy/2),vector2[0]+(maxx/2),(rec2[1]*-1)+(maxy/2));
            y1 = vector1[1];
            y2 = vector2[1];
            break;
        case 'd':
            rec1[0] = 0;
            rec1[1] = 0;
            rec1[2] = 0;
            for(int i=0;i<3;i++){
                rec1[i] = 0;
                for(int j=0;j<3;j++){
                    rec1[i] += matricsdvig[j][i] * vector1[j];
                }
            }
            rec2[0] = 0;
            rec2[1] = 0;
            rec2[2] = 0;
            for(int i=0;i<3;i++){
                rec2[i] = 0;
                for(int j=0;j<3;j++){
                    rec2[i] += matricsdvig[j][i] * vector2[j];
                }
            }
            vector1[0] = rec1[0];
            vector2[0] = rec2[0];
            rec1[1] = vector1[1];
            rec2[1] = vector2[1];
            clearviewport();
            koordinat();
            line(rec1[0]+(maxx/2),-vector1[1]+(maxy/2),rec2[0]+(maxx/2),-vector2[1]+(maxy/2));
            x1 = vector1[0];
            x2 = vector2[0];
            break;
        case 'a':
            rec1[0] = 0;
            rec1[1] = 0;
            rec1[2] = 0;
            for(int i=0;i<3;i++){
                rec1[i] = 0;
                for(int j=0;j<3;j++){
                    rec1[i] += matricsdvig[j][i] * vector1[j];
                }
            }
            rec1[0] -= matricsdvig[2][0] * 2;
            rec2[0] = 0;
            rec2[1] = 0;
            rec2[2] = 0;
            for(int i=0;i<3;i++){
                rec2[i] = 0;
                for(int j=0;j<3;j++){
                    rec2[i] += matricsdvig[j][i] * vector2[j];
                }
            }
            rec2[0] -= matricsdvig[2][0] * 2;
            vector1[0] = rec1[0];
            vector2[0] = rec2[0];
            rec1[1] = vector1[1];
            rec2[1] = vector2[1];
            clearviewport();
            koordinat();
            line(rec1[0]+(maxx/2),-vector1[1]+(maxy/2),rec2[0]+(maxx/2),-vector2[1]+(maxy/2));
            x1 = vector1[0];
            x2 = vector2[0];
            break;
        case 'e':
            clearviewport();
            koordinat();
            mnoz = 2;
            mashtab(mnoz,vector1,vector2,Scaling,Shift,x1,y1,x2,y2);
            line(vector1[0]+(maxx/2),-vector1[1]+(maxy/2),vector2[0]+(maxx/2),-vector2[1]+(maxy/2));
            break;
        case 'q':
            clearviewport();
            koordinat();
            float mnoz;
            mnoz = 0.5;
            mashtab(mnoz,vector1,vector2,Scaling,Shift,x1,y1,x2,y2);
            line(vector1[0]+(maxx/2),-vector1[1]+(maxy/2),vector2[0]+(maxx/2),-vector2[1]+(maxy/2));
            break;
        case 'f':
            simetri(vector1,vector2,maxx,maxy);
            break;
        case 'z':
            clearviewport();
            //setcolor(rand()%20+1);
            koordinat();
            ku=10;

            turned(ku,vector1,vector2,Turn,Scaling,x1,y1,x2,y2,Shift);
            line(vector1[0]+(maxx/2),-vector1[1]+(maxy/2),vector2[0]+(maxx/2),-vector2[1]+(maxy/2));
            break;
        case 'x':
            clearviewport();
            //setcolor(rand()%20+1);
            koordinat();
            ku=-10;

            turned(ku,vector1,vector2,Turn,Scaling,x1,y1,x2,y2,Shift);
            line(vector1[0]+(maxx/2),-vector1[1]+(maxy/2),vector2[0]+(maxx/2),-vector2[1]+(maxy/2));
            break;
        }
    }
}


//otrisovka line
void line(){
    int maxx = getmaxx();
    int maxy = getmaxy();
    maxx += 1;
    maxy +=1;
    int x1, x2, y1, y2;
    std::cout<<"X1 :";
    std::cin>>x1;
    std::cout<<"Y1 :";
    std::cin>>y1;
    std::cout<<"X2 :";
    std::cin>>x2;
    std::cout<<"Y2 :";
    std::cin>>y2;
    line(x1+(maxx/2),-y1+(maxy/2),x2+(maxx/2),-y2+(maxy/2));
    vector1[0] = x1;
    vector1[1] = y1;
    vector1[2] = 1;
    vector2[0] = x2;
    vector2[1] = y2;
    vector2[2] = 1;
    float matricsdvig[3][3];
    matricsdvig[0][0] = 1;
    matricsdvig[0][1] = 0;
    matricsdvig[0][2] = 0;
    matricsdvig[1][0] = 0;
    matricsdvig[1][1] = 1;
    matricsdvig[1][2] = 0;
    matricsdvig[2][0] = 10;
    matricsdvig[2][1] = 10;
    matricsdvig[2][2] = 1;
    float Scaling[3][3];
    for(int i=0;i<3;i++){
        for(int j=0;j<3;j++){
            if((i==2) and (j==2)){
                Scaling[i][j]=1.0;
            }
            else
                Scaling[i][j]=0.0;
        }
    }
    float Turn[3][3];
    for(int i=0;i<3;i++){
        for(int j=0;j<3;j++){
            Turn[i][j]=0.0;
        }
    }
    move(vector1,vector2,matricsdvig,x1,y1,x2,y2,Scaling,Turn);
}

int main()
{
	int gd = DETECT, gm;
	initgraph(&gd, &gm, "");
    koordinat();
    line();
    //move();
	getch();
	closegraph();
}
