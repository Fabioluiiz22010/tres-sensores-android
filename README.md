# Três Sensores — detector de queda para Android

Aplicativo Android que monitora os sensores do aparelho em segundo plano para detectar uma queda e, quando detecta, abre um alerta e pede socorro com a localização.

Avaliação B1 da disciplina **Programação para Dispositivos Móveis III** (ADS, UniSALESIANO Araçatuba), entregue em outubro de 2026. O tema do trabalho era o uso de sensores.

## Como funciona

1. Um serviço em primeiro plano (`MonitorService`) lê acelerômetro e giroscópio continuamente.
2. O `FallDetector` analisa as leituras para identificar o padrão de queda. O sensor de proximidade ajuda a filtrar falsos positivos.
3. Ao detectar a queda, a `AlertaActivity` abre em tela cheia, mesmo com o aparelho bloqueado.
4. O app obtém a localização, envia SMS com um link do Google Maps e registra a ocorrência em uma API externa.

## Sensores e recursos usados

- Acelerômetro, giroscópio, proximidade, luz e pressão (barômetro)
- GPS com `LocationManager`
- SMS com `SmsManager`
- Vibração, notificações e alerta em tela cheia
- API Socorro (`ideaberta.com.br/socorro`) para registrar a ocorrência
- API Open-Meteo para dados do tempo no local

## Stack

- Java
- Android SDK (minSdk 30, targetSdk 36), AppCompat, Material e ConstraintLayout
- Foreground Service
- Gradle

## Permissões

Localização, SMS, notificações, serviço em primeiro plano, vibração, sobreposição de tela e internet. O app também pede para ignorar a otimização de bateria, para o monitoramento não ser interrompido.

## Como rodar

1. Abra a pasta no Android Studio e aguarde a sincronização do Gradle.
2. Execute em um aparelho físico com Android 11 ou mais recente; os sensores não funcionam bem em emulador.
3. Aceite as permissões e conclua a tela de boas-vindas.

## Estrutura

```
app/src/main/java/com/example/tressensores/
  BoasVindasActivity   configuração inicial
  MainActivity         tela principal
  MonitorService       serviço que lê os sensores
  FallDetector         lógica de detecção de queda
  AlertaActivity       alerta em tela cheia
  ApiClient            chamadas às APIs
  Estado               estado compartilhado do monitoramento
```

## Observações

- Projeto acadêmico. Não substitui um dispositivo de emergência.
- O envio de SMS pode gerar custo na operadora.

## Autor

Fabio Luiz Florêncio da Silva · [github.com/Fabioluiiz22010](https://github.com/Fabioluiiz22010) · [LinkedIn](https://www.linkedin.com/in/fabio-l-florencio/)
