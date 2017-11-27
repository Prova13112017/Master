# Master
import java.net.*;
import java.io.*;
//posto :12
public class HuangClient {

	public static void main(String[] args) throws SocketException {
		byte[] dataIN=new byte[1024];// 256 caraterri
		byte[] dataOUT=new byte[1024];//le caraterri usa unicod = 2byte per carratere
		int portaServer=7000;
		InetdAdress ipServer=new InetdAdress("127.0.0.1");
		
		DatagramSocket socketClient =new DatagramSocket(dataOUT,dataOUT.length,ipServer,portaServer);
		DatagramPacket mandaPacchetto =new DatagramPacket(dataOUT,dataOUT.length);
		int numRand=(int)Math.random()%10+1;
		
		String numString=new String(numRand+"");//mette in stringa 
		dataOUT=numString.getBytes();			//diventa in bytes
		
		
		socketClient.send(mandaPacchetto);
		
		for(int numVolta=0;numVolta<numRand;numVolta++){
			numRand=(int)Math.random()%10+1;
			numString=new String(numRand+"");
			dataOUT=numString.getBytes();			
			
			dataOUT[numVolta];
		}
		socketClient.send(mandaPacchetto);
	}
