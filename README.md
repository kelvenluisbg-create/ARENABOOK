# ArenaBook (Demo)

MVP funcional (demo) para agendamento de arenas/quadras com:

- Lista de arenas e quadras
- Agenda por dia/horário
- Reserva com **anti-double-booking** (constraint UNIQUE no SQLite)
- Pagamentos (demo):
  - **PIX**: cria um hold com expiração (~5 min). Você “paga” na tela **Minhas reservas**.
  - **CARD**: confirma na hora (demo).
  - **PAY_ON_SITE**: vai para aprovação do gestor (tela **Admin**).

> Observação: o Pix aqui é **simulado** (payload textual). Para produção, integrar um PSP / gateway e gerar EMV real.

## Rodar localmente

```bash
npm install
npm run dev
```

Abra http://localhost:3000

## Admin

- Rota: `/admin`
- Token padrão: `admin123`
- Para trocar: `ADMIN_TOKEN=seu_token npm run dev`

## Banco

- SQLite local em `data/arenabook.sqlite`
- Seed automático na primeira execução

## Endpoints principais

- `GET /api/venues`
- `GET /api/venues/:venueId`
- `GET /api/bookings?venueId=...&date=YYYY-MM-DD`
- `GET /api/bookings?userOnly=1`
- `POST /api/bookings`
- `POST /api/bookings/:id/pay`
- `POST /api/bookings/:id/approve` (admin)
- `POST /api/bookings/:id/cancel`
- `POST /api/maintenance/expire-holds`

