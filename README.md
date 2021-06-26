package Producao;

import java.util.Scanner;
import java.util.function.BooleanSupplier;

public class conversorTDD {
	
	static Scanner ler = new Scanner(System.in);
	
	int valor = 0;
	
	
	String EnArabico = " ";
	String SaRomano = " ";
	int SaArabico =2;
	
	
	public String converteRomano(String tSaArabico) {

	
		double divisor=0;
		int resul = 0;
		String romano = "";
		
		valor = Integer.parseInt(tSaArabico);
		

	 if(valor>=1000) {
		valor = valor % 1000;
		 romano = romano + "M";
		 
	 }if(valor>=900) {
		 valor = valor % 900; 
		 romano = romano + "CM";
	 }
	 resul = (int) (valor/500);
		valor = valor % 500;
		if(resul == 1) {
			romano = romano + "D";		
}	
		resul = (int) (valor/100);
		valor = valor % 100;
		
		if(resul == 4) {
			romano = romano + "CD";
		}else if(resul >=1 ) {
			
			for(int x=0; x<resul ;x++) {
				romano = romano + "C";
			}
		}
		
		resul = (int) (valor/90); 
		valor = valor%90;
		
		if(resul == 1) {
			romano = romano + "XC";
		}
		
		resul = (int) (valor/50); 
		valor = valor%50;
		
		if(resul == 1) {
			romano = romano + "L";
		}
		
		resul = (int) (valor/10);
		valor = valor % 10;
		
		if(resul == 4) {
			romano = romano + "XL";
		}else if(resul >=1 ) {
			
			for(int x=0; x<resul ;x++) {
				romano = romano + "X";
			}
		}
		resul = (int) (valor/9); 
		valor = valor%9;
		
		if(resul == 1) {
			romano = romano + "IX";
		}
		
		resul = (int) (valor/5); 
		valor = valor%5;
		
		if(resul == 1) {
			romano = romano + "V";
		}
			
			resul = (int) (valor/1);
			valor = valor % 1;
			
			if(resul == 4) {
				romano = romano + "IV";
			}else if(resul >=1 ) {
				
				for(int x=0; x<resul ;x++) {
					romano = romano + "I";
				}
			}
	 
	 return romano;}

	
	public int converteArabico (String tSaRomano) {
		
		String romano = tSaRomano;
		int resul = 0;
		int caracter = romano.length();
		
		for(int x=0; x<caracter; x++) {
			char teste = romano.charAt(x);
			char proximo=0;
				
			switch(teste) {
			
			case 'I':{
				if(caracter>x+1) {
					if(romano.charAt(x+1)=='V') {
						System.out.println();
					resul = resul + 4;
					x++;
				}else if(romano.charAt(x+1)=='X') {
					resul = resul + 9;
					x++;
				}else {
					resul=resul +1;
				}}else {
					resul=resul +1;
				}
				break;
			}	
			case 'V':{
				resul = resul + 5;
				break;	
			}
				
			case 'X':{
				if(caracter>x+1) {
					if(romano.charAt(x+1)=='L') {
						System.out.println();
					resul = resul + 40;
					x++;
				}else if(romano.charAt(x+1)=='C') {
					resul = resul + 90;
					x++;
				}else {
					resul=resul +10;
				}}else {
					resul=resul +10;
				}
				break;
			}	
			case 'L':{
				resul = resul + 50;
				break;	
			}
			
			case 'C':{
				if(caracter>x+1) {
					if(romano.charAt(x+1)=='D') {
						System.out.println();
					resul = resul + 400;
					x++;
				}else if(romano.charAt(x+1)=='M') {
					resul = resul + 900;
					x++;
				}else {
					resul=resul +100;
				}}else {
					resul=resul +100;
				}
				break;
			}
			case 'D':{
				resul = resul + 500;
				break;	
			}	
			case 'M':{
				resul = resul + 1000;
				break;
			}
		
	}
}
	
	return resul;
	}
}
