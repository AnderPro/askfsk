*************FUNCION ASK***********************************




function ask(vector,f)


vector=[1,0,1,0];
f=2;

t=0:2*pi/99:2*pi;
cp=[];sp=[];
mod=[];mod1=[];bit=[];
 
for n=1:length(vector);
    if vector(n)==0;
        die=zeros(1,100);   %Modulante
        se=zeros(1,100);    %Señal
    else
        vector(n)==1;
        die=ones(1,100);    %Modulante
        se=ones(1,100);     %Señal
    end
    
    c=sin(f*t);
    cp=[cp die];
    mod=[mod c];
    bit=[bit se];
end

ask= cp.*mod;


subplot(2,1,1);plot(bit,'LineWidth',1.5);grid on;
title('Señal Binaria');
axis([0 100*length(vector) -2.5 2.5]);
   
subplot(2,1,2);plot(ask,'LineWidth',1.5);grid on;
title('ASK ');
axis([0 100*length(vector) -2.5 2.5]);



************************FUNCION FSK***************************************************************



function fsk(g,f0,f1)

g=[1,0,1];
f0=1;
f1=2;
t=0:2*pi/99:2*pi;
cp=[];sp=[];
mod=[];mod1=[];bit=[];
 
for n=1:length(g);
    if g(n)==0;
        die=ones(1,100);
        c=sin(f0*t);
        se=zeros(1,100);
    else g(n)==1;
        die=ones(1,100);
        c=sin(f1*t);
        se=ones(1,100);
    end
    cp=[cp die];
    mod=[mod c];
    bit=[bit se];
end
 
fskp=cp.*mod;
subplot(2,1,1);plot(bit,'LineWidth',1.5);grid on;
title('Señal Binaria');
axis([0 100*length(g) -2.5 2.5]);
 
subplot(2,1,2);plot(fskp,'LineWidth',1.5);grid on;
title('FSK ');
axis([0 100*length(g) -2.5 2.5]);
