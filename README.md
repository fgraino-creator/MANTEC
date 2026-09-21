# MANTEC — proyecto integrado inicial

Proyecto fuente inicial de Flutter + esquema SQL de Supabase. **No es un APK ni una app de producción.**

## Estado real
- Pantalla de configuración, inicio de sesión con Supabase y panel de módulos (sin datos reales).
- Migración inicial para instalaciones, usuarios/roles, equipos, órdenes, tareas por equipo, planes, eventos, aprobaciones y notificaciones.
- Restricciones SQL básicas de códigos y unicidad. RLS activada sin políticas: el acceso a tablas desde el cliente está bloqueado deliberadamente.
- NO implementados todavía: alta de usuarios, políticas de permisos, funciones transaccionales de emisión/cierre, firmas, PDF, adjuntos, sincronización offline, alertas automáticas, correo, push ni pantallas operativas de cada módulo.

## Reglas de códigos
Tipos Pr, Co, Pd; sectores El, E, M, V, TA, ME; año de dos dígitos; correlativo mínimo dos dígitos, sin ceros superfluos salvo el relleno inicial. Ejemplo CoM2601, CoM26100. Correlativos independientes por tipo/sector/año. Código globalmente único dentro de una instalación. Solo editable en borrador.

## Arranque de desarrollo
1. Instalar Flutter y SDKs Android/iOS según plataforma; ejecutar `flutter create .` dentro de esta carpeta para generar carpetas nativas y archivos de plataforma.
2. Crear proyecto Supabase **de prueba**, aplicar la migración SQL y definir políticas RLS, funciones del servidor y usuarios antes de permitir acceso a registros.
3. Ejecutar `flutter pub get` y `flutter run --dart-define=SUPABASE_URL=... --dart-define=SUPABASE_ANON_KEY=...`.
4. Nunca introducir `service_role` ni credenciales privadas en el cliente.

Para compilar iOS se necesita un entorno macOS/Xcode y configuración de firma de Apple. Android requiere SDK y configuración de firma para distribución.
