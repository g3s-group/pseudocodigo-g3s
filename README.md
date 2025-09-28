# 📌 Pseudocódigo - Sistema de Agendamento e Lembretes

---

## a) Agendamento de Nova Consulta

```pseudocode
FUNÇÃO AgendarConsulta(id_paciente, id_profissional, data_hora_desejada)
  
  // Passo 1: Verificar se o profissional está disponível
  horario_ocupado = VerificarAgendaProfissional(id_profissional, data_hora_desejada)
  SE horario_ocupado == VERDADEIRO ENTÃO
    RETORNAR ERRO "Horário indisponível para este profissional."
  FIM SE

  // Passo 2: Verificar se o paciente já tem outra consulta no mesmo horário
  paciente_tem_conflito = VerificarAgendaPaciente(id_paciente, data_hora_desejada)
  SE paciente_tem_conflito == VERDADEIRO ENTÃO
    RETORNAR ERRO "Paciente já possui um agendamento neste horário."
  FIM SE

  // Passo 3: Criar o registro da consulta
  CriarRegistroConsulta(id_paciente, id_profissional, data_hora_desejada, status="Agendado")
  
  RETORNAR SUCESSO "Consulta agendada com sucesso!"
FIM FUNÇÃO
```

---

## b) Processo de Envio de Lembretes

```pseudocode
PROCESSO EnviarLembretesDiarios()
  
  // Passo 1: Definir a data-alvo para os lembretes (consultas nas próximas 24h)
  data_alvo = DATA_ATUAL + 24 horas

  // Passo 2: Buscar todas as consultas agendadas para a data-alvo
  lista_consultas = BuscarConsultasPorData(data_alvo)

  // Passo 3: Iterar sobre a lista e enviar notificações
  PARA CADA consulta EM lista_consultas
    paciente = BuscarDadosPaciente(consulta.id_paciente)
    mensagem = FormatarMensagem(paciente.nome, consulta.data_hora)
    EnviarNotificacao(paciente.contato, mensagem) // Exemplo: SMS, WhatsApp, Email
  FIM PARA

FIM PROCESSO
```

---
