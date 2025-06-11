# Subasta Descentralizada en Solidity

Este repositorio contiene un contrato inteligente de subasta desarrollado en Solidity 0.8.20, desplegable en la red Sepolia. Fue creado como parte del Trabajo Final del Módulo 2.

## 🎯 Objetivo del Contrato

Permitir que múltiples usuarios participen en una subasta con ETH, respetando las siguientes reglas:

- Cada nueva oferta debe superar en al menos un 5% a la mejor oferta actual.
- Si una oferta válida se realiza en los últimos 10 minutos, la subasta se extiende automáticamente.
- Al finalizar, el ganador transfiere su oferta menos una comisión del 2% al propietario, y el resto de participantes puede recuperar el 98% de sus depósitos.

## ⚙️ Funcionalidades Principales

- `makeBid()`: Permite realizar una oferta pagando con ETH. Solo se aceptan ofertas válidas mientras la subasta está activa.
- `endAuction()`: Finaliza la subasta. Solo el dueño del contrato puede ejecutarla.
- `retrieveFunds()`: Permite reclamar el reembolso luego de finalizada la subasta.
- `withdrawSurplus()`: Habilita a los participantes a retirar el exceso de fondos si han ofertado más de una vez.
- `getTopBid()`: Muestra la oferta más alta y el oferente líder.

## 🔐 Seguridad

- Uso de modificadores `auctionActive` y `restrictedToOwner`.
- Patrón de retiro (`withdraw pattern`) para evitar vulnerabilidades.
- Control de excepciones para prevenir mal uso del contrato.

## 🧾 Eventos

- `BidPlaced`: Se emite cuando un usuario realiza una oferta válida.
- `BiddingClosed`: Marca el final de la subasta.
- `FundsRetrieved`: Indica un reembolso exitoso a un oferente no ganador.

## 📦 Estructura Interna

- `struct Bid`: Representa una oferta con dirección y cantidad.
- `mapping totalFundsPerUser`: Suma total ofertada por cada usuario.
- `mapping userBids`: Historial de ofertas individuales por usuario.
- `mapping pendingReturns`: Fondos disponibles para devolución.

## 🚀 Despliegue

1. Compilar con Solidity 0.8.26.
2. Desplegar en la red Sepolia (por ejemplo, usando Remix o Hardhat).
3. Verificar el contrato en Etherscan Sepolia.
4. Compartir la URL verificada en el Campus.

---

> Este contrato promueve la transparencia, automatiza los reembolsos y evita que los participantes puedan realizar "sniping" en los últimos segundos sin competencia.

