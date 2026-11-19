# Barbearia União — configuração

## 1. Criar o projeto Supabase

Crie um projeto Supabase exclusivo para a Barbearia União. No SQL Editor, execute o arquivo `supabase_barbearia_uniao.sql`.

O script cadastra Warlei Fernandes como barbeiro, mas não presume horários, serviços ou preços. Esses dados devem ser cadastrados no painel administrativo.

## 2. Configurar a aplicação

No arquivo `supabase-config.js`, substitua:

- `url` pela Project URL do projeto Supabase;
- `anonKey` pela chave publishable (ou anon) do mesmo projeto.

Não use chaves secretas nem a chave `service_role` no navegador.

## 3. Liberar o acesso do administrador

1. Em Supabase > Authentication, crie o usuário do Warlei com o e-mail que ele usará no painel.
2. Copie o UUID desse usuário.
3. Use o exemplo comentado no final do SQL para inserir o UUID em `public.uniao_membros`, com `is_admin = true`.
4. Acesse `painel.html`, entre com o e-mail e a senha e cadastre serviços e horários.

Para cada barbeiro adicional, crie a conta no Authentication, cadastre o barbeiro e associe a conta na tabela `uniao_membros`, com `is_admin = false`.

## 4. Publicar

Publique os arquivos desta pasta em uma hospedagem estática com HTTPS (por exemplo, Vercel). As páginas são `index.html`, `agendar.html` e `painel.html`.

O agendamento público só libera horários depois que houver serviços e expediente cadastrados. O painel usa Supabase Auth e as políticas RLS do script para restringir os dados de cada barbeiro e do administrador.
