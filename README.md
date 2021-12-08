%fonction qui calcule le cout 
function [Va11,Va21,Va31,Va41]=countm2p2(i,j,x1,x2,h1,h2,u1,u2,drej,dr,dm,q12,q13,q21,q24,q31,q34,q42,q43,Vp1,Vp2,Vp3,Vp4,Nx1,Nx2,rho,cp1,cm1,cm2,cr1,cr2,cp);
VV=[];
    if x1 > 0
     gc1=cp1*x1; %fonction coût instantané
    else
     gc1=-cm1*x1;
    end 
     if x2 > 0
     gc2=cp1*x2;
    else
     gc2=-cm2*x2;
     end
     
 if i==1
    if j==1
     VV(1)=Vp1(i+1,j);               %vh(x1+h1,x2,1)
     VV(2)=2*Vp1(i,j)-Vp1(i+1,j);    
     VV(3)=Vp1(i,j+1);               %vh(x1,x2+h2,1)
     VV(4)=2*Vp1(i,j)-Vp1(i,j+1);
     VV(5)=Vp2(i,j);                 %vh(x1,x2,2)
     VV(6)=Vp3(i,j);                 %vh(x1,x2,3)
     
     VV(7)=Vp2(i+1,j);
     VV(8)=2*Vp2(i,j)-Vp2(i+1,j);
     VV(9)=Vp2(i,j+1);  
     VV(10)=2*Vp2(i,j)-Vp2(i,j+1);
     VV(11)=Vp1(i,j);
     VV(12)=Vp4(i,j);
     
     VV(13)=Vp3(i+1,j);
     VV(14)=2*Vp3(i,j)-Vp3(i+1,j);
     VV(15)=Vp3(i,j+1);
     VV(16)=2*Vp3(i,j)-Vp3(i,j+1);
     VV(17)=Vp1(i,j);
     VV(18)=Vp4(i,j);          
     
     VV(19)=2*Vp4(i,j)-Vp4(i+1,j);
     VV(20)=Vp4(i,j+1);             %vh(x1,x2+h2,4)
     VV(21)=2*Vp4(i,j)-Vp4(i,j+1);
     VV(22)=Vp2(i,j);               %vh(x1,x2,2) 
     VV(23)=Vp3(i,j);               %vh(x1,x2,3)
        
     elseif j==Nx2
     VV(1)=Vp1(i+1,j);  
     VV(2)=2*Vp1(i,j)-Vp1(i+1,j);
     VV(3)=2*Vp1(i,j)-Vp1(i,j-1);
     VV(4)=Vp1(i,j-1);
     VV(5)=Vp2(i,j);
     VV(6)=Vp3(i,j);
     
     VV(7)=Vp2(i+1,j);
     VV(8)=2*Vp2(i,j)-Vp2(i+1,j);
     VV(9)=2*Vp2(i,j)-Vp2(i,j-1);  
     VV(10)=Vp2(i,j-1);
     VV(11)=Vp1(i,j);
     VV(12)=Vp4(i,j);
     
     VV(13)=Vp3(i+1,j);
     VV(14)=2*Vp3(i,j)-Vp3(i+1,j);
     VV(15)=2*Vp3(i,j)-Vp3(i,j-1);
     VV(16)=Vp3(i,j-1);
     VV(17)=Vp1(i,j);
     VV(18)=Vp4(i,j);
     
     VV(19)=2*Vp4(i,j)-Vp4(i+1,j);
     VV(20)=2*Vp4(i,j)-Vp4(i,j-1);
     VV(21)=Vp4(i,j-1);
     VV(22)=Vp2(i,j);
     VV(23)=Vp3(i,j);
     
     else
     VV(1)=Vp1(i+1,j);  
     VV(2)=2*Vp1(i,j)-Vp1(i+1,j);
     VV(3)=Vp1(i,j+1);
     VV(4)=Vp1(i,j-1);
     VV(5)=Vp2(i,j);
     VV(6)=Vp3(i,j);
     
     VV(7)=Vp2(i+1,j);
     VV(8)=2*Vp2(i,j)-Vp2(i+1,j);
     VV(9)=Vp2(i,j+1);  
     VV(10)=Vp2(i,j-1);
     VV(11)=Vp1(i,j);
     VV(12)=Vp4(i,j);
     
     VV(13)=Vp3(i+1,j);
     VV(14)=2*Vp3(i,j)-Vp3(i+1,j);
     VV(15)=Vp3(i,j+1);
     VV(16)=Vp3(i,j-1);
     VV(17)=Vp1(i,j);
     VV(18)=Vp4(i,j);
     
     VV(19)=2*Vp4(i,j)-Vp4(i+1,j);
     VV(20)=Vp4(i,j+1);
     VV(21)=Vp4(i,j-1);
     VV(22)=Vp2(i,j);
     VV(23)=Vp3(i,j);
     
    end
 elseif i==Nx1
    if j==1
     
     VV(1)=2*Vp1(i,j)-Vp1(i-1,j);  
     VV(2)=Vp1(i-1,j);
     VV(3)=Vp1(i,j+1);
     VV(4)=2*Vp1(i,j)-Vp1(i,j+1);
     VV(5)=Vp2(i,j);
     VV(6)=Vp3(i,j);
     
     VV(7)=2*Vp2(i,j)-Vp2(i-1,j);
     VV(8)=Vp2(i-1,j);
     VV(9)=Vp2(i,j+1);  
     VV(10)=2*Vp2(i,j)-Vp2(i,j+1);
     VV(11)=Vp1(i,j);
     VV(12)=Vp4(i,j);
     
     VV(13)=2*Vp3(i,j)-Vp3(i-1,j);
     VV(14)=Vp3(i-1,j);
     VV(15)=Vp3(i,j+1);
     VV(16)=2*Vp3(i,j)-Vp3(i,j+1);
     VV(17)=Vp1(i,j);
     VV(18)=Vp4(i,j);
     
     VV(19)=Vp4(i-1,j);
     VV(20)=Vp4(i,j+1);
     VV(21)=2*Vp4(i,j)-Vp4(i,j+1);
     VV(22)=Vp2(i,j);
     VV(23)=Vp3(i,j);
        
     elseif j==Nx2
     
     VV(1)=2*Vp1(i,j)-Vp1(i-1,j);  
     VV(2)=Vp1(i-1,j);
     VV(3)=2*Vp1(i,j)-Vp1(i,j-1);
     VV(4)=Vp1(i,j-1);
     VV(5)=Vp2(i,j);
     VV(6)=Vp3(i,j);
     
     VV(7)=2*Vp2(i,j)-Vp2(i-1,j);
     VV(8)=Vp2(i-1,j);
     VV(9)=2*Vp2(i,j)-Vp2(i,j-1);  
     VV(10)=Vp2(i,j-1);
     VV(11)=Vp1(i,j);
     VV(12)=Vp4(i,j);
     
     VV(13)=2*Vp3(i,j)-Vp3(i-1,j);
     VV(14)=Vp3(i-1,j);
     VV(15)=2*Vp3(i,j)-Vp3(i,j-1);
     VV(16)=Vp3(i,j-1);
     VV(17)=Vp1(i,j);
     VV(18)=Vp4(i,j);
     
     VV(19)=Vp4(i-1,j);
     VV(20)=2*Vp4(i,j)-Vp4(i,j-1);
     VV(21)=Vp4(i,j-1);
     VV(22)=Vp2(i,j);
     VV(23)=Vp3(i,j);
         
    else
     VV(1)=2*Vp1(i,j)-Vp1(i-1,j);  
     VV(2)=Vp1(i-1,j);
     VV(3)=Vp1(i,j+1);
     VV(4)=Vp1(i,j-1);
     VV(5)=Vp2(i,j);
     VV(6)=Vp3(i,j);
     
     VV(7)=2*Vp2(i,j)-Vp2(i-1,j);
     VV(8)=Vp2(i-1,j);
     VV(9)=Vp2(i,j+1);  
     VV(10)=Vp2(i,j-1);
     VV(11)=Vp1(i,j);
     VV(12)=Vp4(i,j);
     
     VV(13)=2*Vp3(i,j)-Vp3(i-1,j);
     VV(14)=Vp3(i-1,j);
     VV(15)=Vp3(i,j+1);
     VV(16)=Vp3(i,j-1);
     VV(17)=Vp1(i,j);
     VV(18)=Vp4(i,j);
     
     VV(19)=Vp4(i-1,j);
     VV(20)=Vp4(i,j+1);
     VV(21)=Vp4(i,j-1);
     VV(22)=Vp2(i,j);
     VV(23)=Vp3(i,j);
        
    end
 else
    if j==1
     VV(1)=Vp1(i+1,j);  
     VV(2)=Vp1(i-1,j);
     VV(3)=Vp1(i,j+1);
     VV(4)=2*Vp1(i,j)-Vp1(i,j+1);
     VV(5)=Vp2(i,j);
     VV(6)=Vp3(i,j);
     
     VV(7)=Vp2(i+1,j);
     VV(8)=Vp2(i-1,j);
     VV(9)=Vp2(i,j+1);  
     VV(10)=2*Vp2(i,j)-Vp2(i,j+1);
     VV(11)=Vp1(i,j);
     VV(12)=Vp4(i,j);
     
     VV(13)=Vp3(i+1,j);
     VV(14)=Vp3(i-1,j);
     VV(15)=Vp3(i,j+1);
     VV(16)=2*Vp3(i,j)-Vp3(i,j+1);
     VV(17)=Vp1(i,j);
     VV(18)=Vp4(i,j);
     
     VV(19)=Vp4(i-1,j);
     VV(20)=Vp4(i,j+1);
     VV(21)=2*Vp4(i,j)-Vp4(i,j+1);
     VV(22)=Vp2(i,j);
     VV(23)=Vp3(i,j);
     
     elseif j==Nx2
     VV(1)=Vp1(i+1,j);  
     VV(2)=Vp1(i-1,j);
     VV(3)=2*Vp1(i,j)-Vp1(i,j-1);
     VV(4)=Vp1(i,j-1);
     VV(5)=Vp2(i,j);
     VV(6)=Vp3(i,j);
     
     VV(7)=Vp2(i+1,j);
     VV(8)=Vp2(i-1,j);
     VV(9)=2*Vp2(i,j)-Vp2(i,j-1);  
     VV(10)=Vp2(i,j-1);
     VV(11)=Vp1(i,j);
     VV(12)=Vp4(i,j);
     
     VV(13)=Vp3(i+1,j);
     VV(14)=Vp3(i-1,j);
     VV(15)=2*Vp3(i,j)-Vp3(i,j-1);
     VV(16)=Vp3(i,j-1);
     VV(17)=Vp1(i,j);
     VV(18)=Vp4(i,j);
     
     VV(19)=Vp4(i-1,j);
     VV(20)=2*Vp4(i,j)-Vp4(i,j-1);
     VV(21)=Vp4(i,j-1);
     VV(22)=Vp2(i,j);
     VV(23)=Vp3(i,j); 
         
    else
     VV(1)=Vp1(i+1,j);  
     VV(2)=Vp1(i-1,j);
     VV(3)=Vp1(i,j+1);
     VV(4)=Vp1(i,j-1);
     VV(5)=Vp2(i,j);
     VV(6)=Vp3(i,j);
     
     VV(7)=Vp2(i+1,j);
     VV(8)=Vp2(i-1,j);
     VV(9)=Vp2(i,j+1);  
     VV(10)=Vp2(i,j-1);
     VV(11)=Vp1(i,j);
     VV(12)=Vp4(i,j);
     
     VV(13)=Vp3(i+1,j);
     VV(14)=Vp3(i-1,j);
     VV(15)=Vp3(i,j+1);
     VV(16)=Vp3(i,j-1);
     VV(17)=Vp1(i,j);
     VV(18)=Vp4(i,j);
     
     VV(19)=Vp4(i-1,j);
     VV(20)=Vp4(i,j+1);
     VV(21)=Vp4(i,j-1);
     VV(22)=Vp2(i,j);
     VV(23)=Vp3(i,j); 
        
    end 
 end 
 
Q11=1/(rho+q12+q13+(abs(u1-dm)/h1)+(abs(u2-dr)/h2));
Q21=1/(rho+q21+q24+(abs(u1-dm)/h1)+(abs(dr)/h2));
Q31=1/(rho+q31+q34+(abs(dm)/h1)+(abs(u2-dr)/h2));
Q41=1/(rho+q42+q43+abs(dm/h1)+(abs(dr)/h2));

if (u1-dm>=0) %In+
 Vs1=1; 
 Vs2=0;
else              %In-
 Vs1=0;
 Vs2=1;
end
 if (u2-dr>=0) %In+
 Vs3=1;
 Vs4=0;
 else               %In-
 Vs3=0;
 Vs4=1;
 end
 

 
%fonction valeur aux 4 modes

Va11=Q11*((abs(u1-dm)/h1)*(Vs1*VV(1)+Vs2*VV(2))+(abs(u2-dr)/h2)*(Vs3*VV(3)+Vs4*VV(4))+gc1+gc2+cp*drej+q12*VV(5)+q13*VV(6));

Va21=Q21*((abs(u1-dm)/h1)*(Vs1*VV(7)+Vs2*VV(8))+(abs(dr)/h2)*(VV(10))+gc1+gc2+cr1+cp*drej+q21*VV(11)+q24*VV(12));

Va31=Q31*((abs(dm)/h1)*(VV(14))+(abs(u2-dr)/h2)*(Vs3*VV(15)+Vs4*VV(16))+gc1+gc2+cr2+cp*drej+q31*VV(17)+q34*VV(18));

Va41=Q41*((dm/h1)*VV(19)+(abs(dr)/h2)*(VV(21))+gc1+gc2+cr1+cr2+cp*drej+q42*VV(22)+q43*VV(23));


