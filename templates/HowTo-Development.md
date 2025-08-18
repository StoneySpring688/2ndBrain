---
title: "Cómo [configurar/implementar/desplegar] - tarea de desarrollo específica"
type: howto
tags: [tool/herramienta, platform/sistema, topic/development]
status: draft
last_reviewed: YYYY-MM-DD
prerequisites: [git, nodejs, docker]
estimated_time: "45 minutes"
platforms: [macos, linux, windows]
last_tested: YYYY-MM-DD
difficulty: intermediate
tech_stack: [language, framework, database, tools]
---

# Cómo [configurar/implementar/desplegar tarea de desarrollo]

Descripción breve del objetivo técnico y el resultado esperado del setup/implementación.

## 🎯 Objetivo

Al completar esta guía podrás:
- [ ] Configurar el entorno de desarrollo completo
- [ ] Implementar la funcionalidad objetivo
- [ ] Validar que todo funciona correctamente
- [ ] Desplegar en el entorno apropiado (si aplica)

## 📋 Prerequisitos

### Software y herramientas
- [ ] **Git** (versión 2.30+) - [Instalación](link)
- [ ] **Node.js** (versión 18+) y npm/yarn
- [ ] **Docker** (si se requiere containerización)
- [ ] **IDE/Editor** recomendado con extensiones
- [ ] **Base de datos** (PostgreSQL/MongoDB/etc.) si aplica

### Conocimientos previos
- [ ] Familiaridad con [concepto base](../../10-Concepts/concepto.md)
- [ ] Experiencia básica con la tech stack
- [ ] Comprensión de conceptos de desarrollo web/backend

### Recursos y credenciales
- [ ] Repositorio base o plantilla
- [ ] Variables de entorno necesarias
- [ ] Credenciales de servicios externos
- [ ] Acceso a servicios de deploy (Vercel, AWS, etc.)

## 🚀 Configuración inicial

### Paso 1: Clonar y configurar proyecto

```bash
# Clonar repositorio o crear desde template
git clone https://github.com/usuario/proyecto.git
cd proyecto

# Instalar dependencias
npm install
# o
yarn install
```

### Paso 2: Configurar variables de entorno

```bash
# Copiar archivo de configuración
cp .env.example .env

# Editar variables necesarias
# Importante: NO commitear credenciales reales
```

**Variables requeridas:**
- `DATABASE_URL`: Conexión a base de datos
- `API_KEY`: Clave de servicio externo
- `JWT_SECRET`: Para autenticación
- `NODE_ENV`: development/production

### Paso 3: Configurar base de datos

```bash
# Levantar base de datos local (Docker)
docker-compose up -d postgres

# Ejecutar migraciones
npm run migrate
# o
npx prisma migrate dev
```

## 🔧 Implementación paso a paso

### Paso 4: Estructura del proyecto

Explicar la arquitectura y organización de archivos:

```
proyecto/
├── src/
│   ├── components/     # Componentes reutilizables
│   ├── pages/         # Rutas/páginas
│   ├── services/      # Lógica de negocio
│   ├── utils/         # Funciones auxiliares
│   └── types/         # Definiciones TypeScript
├── tests/
├── docs/
├── package.json
└── README.md
```

### Paso 5: Implementar funcionalidad core

```javascript
// src/services/coreService.js
class CoreService {
  constructor(config) {
    this.config = config;
    this.client = new ExternalAPI(config.apiKey);
  }

  async processData(input) {
    try {
      // Validar entrada
      const validatedInput = this.validateInput(input);
      
      // Procesamiento principal
      const result = await this.client.process(validatedInput);
      
      // Transformar resultado
      return this.transformResult(result);
      
    } catch (error) {
      console.error('Error procesando datos:', error);
      throw new ProcessingError(error.message);
    }
  }

  validateInput(input) {
    // Implementar validación específica
    if (!input || typeof input !== 'object') {
      throw new ValidationError('Input inválido');
    }
    return input;
  }

  transformResult(result) {
    // Transformar respuesta al formato esperado
    return {
      success: true,
      data: result.data,
      timestamp: new Date().toISOString()
    };
  }
}

export default CoreService;
```

### Paso 6: Configurar testing

```bash
# Instalar dependencias de testing
npm install --save-dev jest supertest

# Crear configuración de Jest
echo 'module.exports = { testEnvironment: "node" };' > jest.config.js
```

```javascript
// tests/coreService.test.js
import CoreService from '../src/services/coreService.js';

describe('CoreService', () => {
  let service;
  
  beforeEach(() => {
    service = new CoreService({
      apiKey: 'test-key',
      environment: 'test'
    });
  });

  test('debe procesar datos válidos correctamente', async () => {
    const input = { message: 'test' };
    const result = await service.processData(input);
    
    expect(result.success).toBe(true);
    expect(result.data).toBeDefined();
  });

  test('debe lanzar error con entrada inválida', async () => {
    await expect(service.processData(null))
      .rejects.toThrow('Input inválido');
  });
});
```

### Paso 7: Scripts de desarrollo

```json
// package.json scripts section
{
  "scripts": {
    "dev": "nodemon src/index.js",
    "start": "node src/index.js", 
    "test": "jest",
    "test:watch": "jest --watch",
    "test:coverage": "jest --coverage",
    "lint": "eslint src/",
    "lint:fix": "eslint src/ --fix",
    "build": "webpack --mode production",
    "migrate": "npx prisma migrate dev"
  }
}
```

## 🧪 Testing y validación

### Ejecutar tests

```bash
# Tests unitarios
npm test

# Tests con coverage
npm run test:coverage

# Tests de integración
npm run test:integration

# Linting
npm run lint
```

### Testing manual

1. **Verificar servidor local:**
   ```bash
   npm run dev
   # Debería estar disponible en http://localhost:3000
   ```

2. **Probar endpoints principales:**
   ```bash
   # Healthcheck
   curl http://localhost:3000/health
   
   # Endpoint principal
   curl -X POST http://localhost:3000/api/process \
     -H "Content-Type: application/json" \
     -d '{"message": "test"}'
   ```

3. **Verificar base de datos:**
   ```bash
   # Conectar a DB local
   psql postgresql://user:pass@localhost:5432/dbname
   
   # Verificar tablas creadas
   \dt
   ```

## 🚀 Deployment

### Deploy a producción

#### Opción 1: Vercel (Frontend/Fullstack)

```bash
# Instalar Vercel CLI
npm install -g vercel

# Deploy
vercel

# Configurar variables de entorno en dashboard
# IMPORTANTE: Usar valores de producción
```

#### Opción 2: Docker + VPS

```dockerfile
# Dockerfile
FROM node:18-alpine

WORKDIR /app

COPY package*.json ./
RUN npm ci --only=production

COPY . .

EXPOSE 3000

CMD ["npm", "start"]
```

```bash
# Build y deploy
docker build -t proyecto:latest .
docker push registry/proyecto:latest

# En servidor
docker pull registry/proyecto:latest
docker-compose up -d
```

#### Opción 3: AWS/GCP/Azure

```bash
# Configurar CLI
aws configure  # o gcloud init, az login

# Deploy usando herramientas específicas
sam deploy  # AWS SAM
gcloud app deploy  # Google App Engine
az webapp up  # Azure Web Apps
```

## 🔧 Troubleshooting

### Problemas comunes

#### Error: "Port 3000 already in use"
```bash
# Encontrar proceso usando el puerto
lsof -ti:3000

# Terminar proceso
kill -9 $(lsof -ti:3000)
```

#### Error: "Database connection failed"
```bash
# Verificar que DB esté corriendo
docker ps | grep postgres

# Verificar variables de entorno
echo $DATABASE_URL

# Probar conexión manual
psql $DATABASE_URL
```

#### Error: "Module not found"
```bash
# Limpiar node_modules y reinstalar
rm -rf node_modules package-lock.json
npm install

# Verificar versión de Node
node --version  # Debe ser 18+
```

### Logs y debugging

```bash
# Ver logs en desarrollo
npm run dev | bunyan  # Si usas bunyan

# Ver logs en producción
docker logs container-name -f

# Debug con inspector de Node
node --inspect src/index.js
```

## 📊 Monitoreo y mantenimiento

### Métricas importantes
- **Response time**: < 200ms para endpoints principales
- **Error rate**: < 1% en producción
- **Memory usage**: < 512MB en condiciones normales
- **CPU usage**: < 70% bajo carga normal

### Health checks
```javascript
// src/routes/health.js
app.get('/health', async (req, res) => {
  const health = {
    status: 'ok',
    timestamp: new Date().toISOString(),
    services: {
      database: await checkDatabase(),
      externalAPI: await checkExternalAPI(),
      redis: await checkRedis()
    }
  };
  
  res.json(health);
});
```

### Actualizaciones
```bash
# Verificar dependencias desactualizadas
npm audit

# Actualizar dependencias seguras
npm update

# Verificar vulnerabilidades
npm audit fix
```

## 🔗 Recursos relacionados

- [Concepto: Arquitectura del sistema](../../10-Concepts/arquitectura.md)
- [Snippet: Configuración de Express](../../30-Snippets/JavaScript/express-setup.md)
- [Proyecto: Ejemplos similares](../../40-Projects/proyectos-similares.md)
- [HowTo: Deploy a AWS](./deploy-aws.md)
- [HowTo: Configurar CI/CD](./setup-cicd.md)

## 📖 Referencias

### Documentación oficial
- [Framework documentation](https://framework.dev/docs)
- [Database ORM docs](https://orm.docs.com)
- [Deployment platform docs](https://platform.docs.com)

### Herramientas utilizadas
- [Postman collection](link) - Para testing de APIs
- [Docker compose file](link) - Para desarrollo local
- [CI/CD pipeline example](link) - Para automatización

---

**Notas de revisión:**
- [ ] Verificar que todos los comandos funcionen en la versión actual
- [ ] Actualizar URLs y referencias a recursos externos
- [ ] Probar el proceso completo en entorno limpio
- [ ] Verificar que las credenciales de ejemplo no sean reales