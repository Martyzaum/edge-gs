# Simulador de ECG para Arduino
Este é um código em C++ para Arduino que simula um sinal de Eletrocardiograma (ECG). O sinal simulado representa uma série de ondas típicas de um ECG, incluindo ondas P, QRS, e T, bem como segmentos e intervalos relacionados. O sinal gerado é projetado para representar um batimento cardíaco de 80 BPM.

# Sinal ECG Simulado
O sinal ECG simulado é representado pela matriz ECG80BPM, que contém 180 pontos de dados. Cada ponto de dados corresponde a um valor de amplitude do sinal em um determinado instante. O sinal é dividido em várias partes:

# Onda APB: Representando a onda P e a primeira parte do complexo QRS.
Retas BC, DE, FG e HI: Segmentos retos representando diferentes partes do ECG.
Retas CQ, QR, RS e SD: Segmentos retos representando diferentes partes do complexo QRS.
Retas ST: Representando o segmento ST.
Onda ETF: Representando a onda T.
Retas FG: Segmento reto após a onda T.
Onda GUH: Representando uma forma de onda adicional após o segmento ST.
Linhas Isoelétricas: Representando períodos de repouso ou inatividade elétrica.
Configuração Inicial
O código configura a comunicação serial para debug a uma taxa de 9600 bps e define o pino 6 como saída para gerar o sinal analógico simulado.

cpp
Copy code
void setup() {
    Serial.begin(9600);
    pinMode(6, OUTPUT);
}
Loop Principal
O loop principal itera sobre os pontos de dados do sinal ECG simulado e os envia para o pino analógico 6 com um atraso de 5 milissegundos entre cada ponto.

cpp
Copy code
void loop() {
    for(int i = 0; i < 180; i++) {
        // Serial.println(ECG80BPM[i]); // Descomente para visualizar os valores no console serial
        delay(5);
        analogWrite(6, ECG80BPM[i]);
    }
}
Lembre-se de que este código é uma simulação e não representa um sinal de ECG real. É destinado apenas para fins educacionais e de demonstração. Para aplicações médicas reais, consulte profissionais de saúde qualificados e utilize equipamentos certificados.