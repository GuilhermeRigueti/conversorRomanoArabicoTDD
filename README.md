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
			romano = romano + "D";}	
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
			}}}
	return resul;
	}}
	
	
	
	

import static org.junit.Assert.assertEquals;
import static org.junit.Assert.assertTrue;
import static org.junit.jupiter.api.Assertions.*;
import org.junit.jupiter.api.BeforeEach;
import org.junit.jupiter.api.Test;
import Producao.conversorTDD;

class ConversorTestes {

	String TesteVArabico = "15"; //Valor aleatorio p/ teste de Arabico p/ romano
	String TesteRRomano = "XV"; //Resultado certo para teste
	String TSaArabico ;
	conversorTDD ar;
	@BeforeEach
	void estanciaArabico () {
		ar = new conversorTDD();}
	@Test
	void TesteconverteRomanoMilAQuinhentosEUm() {
	
	TSaArabico=ar.converteRomano("1000");
	assertEquals(TSaArabico, "M");
	
	TSaArabico=ar.converteRomano("900");
	assertEquals(TSaArabico, "CM");
	
	TSaArabico=ar.converteRomano("990");
	assertEquals(TSaArabico, "CMXC");
	
	TSaArabico=ar.converteRomano("750");
	assertEquals(TSaArabico, "DCCL");
	
	TSaArabico=ar.converteRomano("515");
	assertEquals(TSaArabico, "DXV");
	
	TSaArabico=ar.converteRomano("510");
	assertEquals(TSaArabico, "DX");
	
	TSaArabico=ar.converteRomano("505");
	assertEquals(TSaArabico, "DV");
	
	TSaArabico=ar.converteRomano("504");
	assertEquals(TSaArabico, "DIV");
	
	TSaArabico=ar.converteRomano("501");
	assertEquals(TSaArabico, "DI");}	
	@Test
	void TesteconverteRomanoCemAQuinhentos() {	
	TSaArabico=ar.converteRomano("100");
	assertEquals(TSaArabico, "C");
	
	TSaArabico=ar.converteRomano("101");
	assertEquals(TSaArabico, "CI");
	
	TSaArabico=ar.converteRomano("104");
	assertEquals(TSaArabico, "CIV");
	
	TSaArabico=ar.converteRomano("105");
	assertEquals(TSaArabico, "CV");
	
	TSaArabico=ar.converteRomano("109");
	assertEquals(TSaArabico, "CIX");
	
	TSaArabico=ar.converteRomano("110");
	assertEquals(TSaArabico, "CX");
	
	TSaArabico=ar.converteRomano("150");
	assertEquals(TSaArabico, "CL");
	
	TSaArabico=ar.converteRomano("200");
	assertEquals(TSaArabico, "CC");
	
	TSaArabico=ar.converteRomano("250");
	assertEquals(TSaArabico, "CCL");
	
	TSaArabico=ar.converteRomano("259");
	assertEquals(TSaArabico, "CCLIX");
	
	TSaArabico=ar.converteRomano("300");
	assertEquals(TSaArabico, "CCC");
	
	TSaArabico=ar.converteRomano("400");
	assertEquals(TSaArabico, "CD");
	
	TSaArabico=ar.converteRomano("450");
	assertEquals(TSaArabico, "CDL");
	
	TSaArabico=ar.converteRomano("500");
	assertEquals(TSaArabico, "D");
	}
	
	@Test
	void TesteconverteRomanoDezACem() {
	
	TSaArabico=ar.converteRomano("10");
	assertEquals(TSaArabico, "X");
	
	TSaArabico=ar.converteRomano("11");
	assertEquals(TSaArabico, "XI");
	
	TSaArabico=ar.converteRomano("14");
	assertEquals(TSaArabico, "XIV");
	
	TSaArabico=ar.converteRomano("15");
	assertEquals(TSaArabico, "XV");
	
	TSaArabico=ar.converteRomano("19");
	assertEquals(TSaArabico, "XIX");
	
	TSaArabico=ar.converteRomano("20");
	assertEquals(TSaArabico, "XX");
	
	TSaArabico=ar.converteRomano("40");
	assertEquals(TSaArabico, "XL");
	
	TSaArabico=ar.converteRomano("50");
	assertEquals(TSaArabico, "L");
	
	TSaArabico=ar.converteRomano("51");
	assertEquals(TSaArabico, "LI");
	
	TSaArabico=ar.converteRomano("60");
	assertEquals(TSaArabico, "LX");
	
	TSaArabico=ar.converteRomano("75");
	assertEquals(TSaArabico, "LXXV");
	
	TSaArabico=ar.converteRomano("90");
	assertEquals(TSaArabico, "XC");
	
	TSaArabico=ar.converteRomano("99");
	assertEquals(TSaArabico, "XCIX");
	
	TSaArabico=ar.converteRomano("100");
	assertEquals(TSaArabico, "C");
	
	}
	@Test
	void testeConverteRomanoUmADez() {
		
		TSaArabico=ar.converteRomano("1");
		assertEquals(TSaArabico, "I");
		
		TSaArabico=ar.converteRomano("4");
		assertEquals(TSaArabico, "IV");
		
		TSaArabico=ar.converteRomano("5");
		assertEquals(TSaArabico, "V");
		
		TSaArabico=ar.converteRomano("7");
		assertEquals(TSaArabico, "VII");
		
		TSaArabico=ar.converteRomano("9");
		assertEquals(TSaArabico, "IX");
		
		TSaArabico=ar.converteRomano("10");
		assertEquals(TSaArabico, "X");
		
	}
	@Test
	void TesteACriterioRomano() {
		
	
	TSaArabico=ar.converteRomano(TesteVArabico);
	assertEquals(TSaArabico, TesteRRomano);
	}
	
	
	
	
	conversorTDD ra;
	int TSaRomano = 0;
	
	@BeforeEach
	void estancia () {
		ra = new conversorTDD();
	}
	
	@Test
	void testeConverteArabicoUmANove() {
		
		TSaRomano = ra.converteArabico("I");
		assertEquals(TSaRomano, 1);
		
		TSaRomano = ra.converteArabico("IV");
		assertEquals(TSaRomano, 4);
		
		TSaRomano = ra.converteArabico("III");
		assertEquals(TSaRomano, 3);
		
		TSaRomano = ra.converteArabico("V");
		assertEquals(TSaRomano, 5);
		
		TSaRomano = ra.converteArabico("VI");
		assertEquals(TSaRomano, 6);
		
		TSaRomano = ra.converteArabico("IX");
		assertEquals(TSaRomano, 9);
		
		
	}
	@Test
	void testeConverteArabicoDezANoventaENove() {
		
		TSaRomano = ra.converteArabico("X");
		assertEquals(TSaRomano, 10);
		
		TSaRomano = ra.converteArabico("XI");
		assertEquals(TSaRomano, 11);
		
		TSaRomano = ra.converteArabico("XIV");
		assertEquals(TSaRomano, 14);
		
		TSaRomano = ra.converteArabico("XV");
		assertEquals(TSaRomano, 15);
		
		TSaRomano = ra.converteArabico("XXX");
		assertEquals(TSaRomano, 30);
		
		TSaRomano = ra.converteArabico("XL");
		assertEquals(TSaRomano, 40);
		
		TSaRomano = ra.converteArabico("L");
		assertEquals(TSaRomano, 50);
		
		TSaRomano = ra.converteArabico("XC");
		assertEquals(TSaRomano, 90);
	
		TSaRomano = ra.converteArabico("XCIX");
		assertEquals(TSaRomano, 99);
	}
	
	@Test
	void testeConverteArabicoCemAQuinhentos() {
		
		TSaRomano = ra.converteArabico("C");
		assertEquals(TSaRomano, 100);
		
		TSaRomano = ra.converteArabico("CIX");
		assertEquals(TSaRomano, 109);
		
		TSaRomano = ra.converteArabico("CXLIX");
		assertEquals(TSaRomano, 149);
		
		TSaRomano = ra.converteArabico("CL");
		assertEquals(TSaRomano, 150);
		
		TSaRomano = ra.converteArabico("CCC");
		assertEquals(TSaRomano, 300);
		
		TSaRomano = ra.converteArabico("CD");
		assertEquals(TSaRomano, 400);
		
		TSaRomano = ra.converteArabico("D");
		assertEquals(TSaRomano, 500);
		
		TSaRomano = ra.converteArabico("CDXCVIII");
		assertEquals(TSaRomano, 498);
		
		TSaRomano = ra.converteArabico("D");
		assertEquals(TSaRomano, 500);	
	}
	
	@Test
	void testeConverteArabicoQuinhentosAMil() {
		
		TSaRomano = ra.converteArabico("DI");
		assertEquals(TSaRomano, 501);
		
		TSaRomano = ra.converteArabico("DCCC");
		assertEquals(TSaRomano, 800);
		
		TSaRomano = ra.converteArabico("CM");
		assertEquals(TSaRomano, 900);
		
		TSaRomano = ra.converteArabico("CMLXXXIX");
		assertEquals(TSaRomano, 989);
		
		TSaRomano = ra.converteArabico("CMXCIX");
		assertEquals(TSaRomano, 999);
		
		TSaRomano = ra.converteArabico("M");
		assertEquals(TSaRomano, 1000);
		
	}
	
	@Test
	void testeConverteArabicoMilEUm() {
		TSaRomano = ra.converteArabico("MI");
		assertEquals(TSaRomano, 1001);	
	}}



