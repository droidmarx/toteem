# Sistema de Chamada de Senhas - Somos do Bem

Sistema completo em HTML5 com 3 telas que se comunicam via **MockAPI**.

## Telas

| Arquivo       | Função                                      | Uso recomendado          |
|---------------|---------------------------------------------|--------------------------|
| `totem.html`  | Totem para o paciente gerar a senha         | Tablet / Totem touch     |
| `guiche.html` | Painel dos 2 guichês (chamar e finalizar)   | Computador dos atendentes|
| `painel.html` | Painel público mostrando a senha chamada    | TV / Monitor grande      |

## Configuração do MockAPI (obrigatório)

1. Acesse o projeto:  
   https://mockapi.io/projects/698deef5aded595c25308e9f

2. Clique em **+ New Resource**

3. Nome do resource: **`Senhas`**

4. Adicione os campos abaixo (clique em **Add field**):

| Campo       | Tipo     |
|-------------|----------|
| `numero`    | Number   |
| `tipo`      | String   |
| `status`    | String   |
| `guiche`    | Number   |
| `createdAt` | String   |
| `chamadoEm` | String   |

5. Clique em **Create** / **Save**

Pronto! A API estará disponível em:

```
https://698deef5aded595c25308e9f.mockapi.io/Senhas
```

## Como usar

1. Abra os 3 arquivos HTML no navegador (pode ser local ou hospedado).
2. No **totem.html** o paciente escolhe a fila e gera a senha.
3. No **guiche.html** o atendente clica em **Chamar Próxima**.
4. O **painel.html** atualiza automaticamente mostrando a senha e o guichê.

### Fluxo de status da senha

```
aguardando  →  chamado  →  atendido
   (totem)     (guichê)    (finalizar)
```

## Categorias disponíveis

- TERAPIAS/CONSULTAS AGENDADAS (verde)
- AGENDAMENTO DE CONSULTAS (escuro)
- SOLICITAÇÃO DE LAUDOS E RECEITAS (laranja)
- SERVIÇO SOCIAL (roxo)

## Observações técnicas

- As telas fazem polling na API (2–3 segundos).
- Não precisa de backend próprio.
- Funciona offline no sentido de que o totem tem fallback de numeração local, mas o ideal é a API estar online.
- Para produção real, recomendo trocar o MockAPI por um backend próprio (Node, Firebase, Supabase, etc.).
