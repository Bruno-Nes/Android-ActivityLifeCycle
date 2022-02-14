# Android-ActivityLifeCycle
Um projeto para entender e ver o básico do cilco de vida das activities e seus callbacks

Ciclo de vida
Diferente dos paradigmas de programação que o programa é iniciado com um método main(), como no C ou no kotlin, O Android inicia o código em uma instância da activity, invocando métodos do ciclo de vida dessa activity


Ao longo da vida útil de uma atividade, ela passa por vários estados


Uma série de callbacks são usados para lidar com transições entre estados. 
1 - onCreate() - Obrigatório
   Esse callback é executado pelo sistema quando a activity é criada 
   É aqui que você precisa chamar o método setContentView() para definir o layout da interface do usuário na activity


2 - onStart()
   Esse callback é executado quando o onCreate() termina. Após o onCreate() da activity entra em estado de iniciada e se torna visível
   É aquele que você deve fazer os preparativos finais da activity para ir para o primeiro plano e se tornar interativa com o usuário 


3 - onResume()
   O sistema invoca esse callback imediatamente antes da atividade começar a interagir com o usuário 
   A maior parte da funcionalidade principal de um app e implementada no método onResume()


4 - onPause()
   O sistema invoca esse callback quando a activity sai de foco. Ao perder o foco a activity entra em estado "Pausado". Pode ser que o usuário tenha saído da aplicação
   No estado pausado a activity consome menos recursos, ela continua sendo atualizada 
   Não use o onPause() para salvar dados do app ou do usuário, fazer chamadas de rede ou executar transações de bancos de dados. Isso é feito no onResume() ou durante a interação do usuário com o app, pq a activity perde prioridade, sendo assim, ela mata qualquer chamada que fizer. Pois, algumas dessa chamadas(BroadcastReceiver, callrotine com timer, threads e etc) consomem recursos e já que a tela não está mais sendo "usada" não tem por que a activity continuar usando esses recursos  


Informação importante:
No onCreate você vai fazer operações leves, coisas simples, como: vincular dados a uma lista e chamar o setContentView() que define a UI
No onResume(preferível) ou no onStart é onde será setado as views, suas funcionalidades, requisições e leituras no banco de dados, requisição à API


5 - onStop()
   Quando a activity não está mais visível para o usuário. Isso pode acontecer porque ela está sendo destruída, uma nova atividade está sendo iniciada ou uma atividade já existente está entrando em um estado "Retomado" e está cobrindo a atividade interrompida. 


6 - onDestroy()
   O sistema invoca esse callback antes da activity ser destruída. Para garantir que todos os recursos sejam liberados quando ela for destruída. Para ela ser destruída o método finish() deve ser chamado
