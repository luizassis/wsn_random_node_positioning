function simulacaoPosAleatoNos(quant,R)
% Nome: Luiz Fernando Ferreira Gomes de Assis RA: 823261
% A variável quant é a quantidade de nos que iremos simular,
% a variável m é a tabela representada por uma matriz, das distancia entre os nós
		
	% fazendo a validação para a constante de conectividade
   	if(R>=0 & R<=1)
        
        % mudando para o formato com apenas duas casas decimais
	format bank;
		
	% O vetor x recebe números aleatórios e os ordena.
	% randn - distribuição normal | rand - distribuição uniforme
    	x = sort(rand([1 quant]));
    
	% O vetor y recebe apenas números aleatórios.
    	y = rand([1 quant]);
    
    	% Atribuir a x(1) o valor 0
    	x(1)=0;
    
	% Atribuir a y(1) o valor 0.5
    	y(1)=0.5;
        
    	% Esta função plota os dois vetores em um gráfico, o primeiro 
    	% parâmetro são os elementos do vetor x e o segundo são os elementos 
        % do vetor y, os pontos terão coordenas do tipo (x(i),y(i)) com
        % i variando de 1 a quant. O terceiro parâmetro contém as
        % características do gráfico. 
    	plot(x,y,'black*')
    	xlabel('x');
    	ylabel('y');
    	title('Simulação do Posicionamento dos Nós');
		
	% O for é para estabelecer uma matriz de 2 colunas e quant linhas, ou seja,
	% uma matriz que possui a posição dos quant nós, a primeira coluna possui
	% a coordenada x(horizontal) de cada nó e a segunda coluna possui a coordenada 
	% y(vertical).
	for i=1:quant
    		pos(i,1)=i;
		pos(i,2)=x(i);
		pos(i,3)=y(i);
        end
        
        % O primeiro for é para percorrer as linhas da matriz de distâncias 
	% o segundo for é para percorrer as colunas da matriz de distâncias
    	% lembrando que a matriz é composta da seguinte forma:
    	% m(i,j) = m(j,i) com i,j 1<=i,j<=quant 
    	% pois a distância entre o nó 1 e 2 é a mesma entre o nó 2 e 1
    	% dada pela fórmula D = ((x0 - x1)2 + (y0-y1)2)1/2.
    	for i=1:quant
          	for j=i:quant
			dis(i,j)=sqrt((x(i)-x(j))^2 + (y(i)-y(j))^2);
			dis(j,i)=dis(i,j);
		end
        end
		
       	% O primeiro for percorre as linhas e o segundo for percorre a 
	% as colunas da matriz conectividade. Lembrando que a conectividade 
	% é estabelecida através de uma constante, esta constante assume valores 
	% entre zero e um. Se a distância entre dois nós for menor que a constante 
	% então os nós possuem uma conectividade, caso contrário, não possuem.
	for i=1:quant
		for j=i:quant
			if(dis(i,j)<R)
				con(i,j)=1;
				con(j,i)=con(i,j);
			end
		end
        end
		
        % Apresenta a matriz de conectividade na tela
        con
        
	% Apresenta o número de nós gerados na tela.
	disp(['O numero de nos gerados sao: ',num2str(quant)]);
		
	% É feito um vetor per para adicionarmos os nós que não 
	% possuem conexão com nenhum outro nó. A variável é para 
	% nos dar parâmetro de quantos elementos estão perdidos,
	% a variável ok é acionada inicialmente (recebe valor um),
	% se acharmos na linha i um valor cinco na matriz con2 significa
	% significa que o nó i possui ligacao com algum nó. Apresenta na tela a 
	% a quantidade de nos perdidos.
	cont=0;
        for i=1:quant
			ok=1;
			for j=1:quant
				if(con(i,j)==1 & i~=j)
					ok=0;
				end
			end
			if(ok)
				cont=cont+1;
				per(cont)=i;
			end		
        end
        if(cont==0)
           per(1)=0; 
        end

        disp(['O numero de nos perdidos sao : ',num2str(cont)]);
		
	% Apresenta o número de nós conectados na tela 
	disp(['O numero de nos conectados sao : ',num2str(quant-cont)]);
	
        % As características das matriz de distâncias são apresentadas a seguir:
        % Média, moda, mediana, desvio padrão, variância
        
        cont=1;
        for i=1:quant
            for j=i+1:quant
                aux(cont)=dis(i,j);
                cont=cont+1;
            end
        end
        
        % Apresenta a média das distâncias entre os nós
        media = mean(aux);
	disp(['A media das distancias e : ',num2str(media,2)]);
        
        % Apresenta a moda das distâncias entre os nós
        moda = mode(aux);
	disp(['A moda das distancias e : ',num2str(moda,2)]);
        
        % Apresenta a mediana das distâncias entre os nós
        mediana = median(aux);
	disp(['A mediana das distancias e : ',num2str(mediana,2)]);
        
        % Apresenta o desvio padrão das distâncias entre os nós
        desvio = std(aux);
	disp(['A desvio padrao das distancias e : ',num2str(desvio,2)]);
        
        % Apresenta a variância das distâncias entre os nós
        variancia = var(aux);
		disp(['A variancia das distancias e : ',num2str(variancia,2)]);
            
    else
        disp('O valor da constante de conectividade esta fora do intervalo permitido entre 0 e 1(0<=R<=1)');
    end
    
end
