# 📘 Руководство по настройке MCP серверов в Claude Code для VSCode

## 🎯 Краткая справка

**Проблема:** Claude Code в VSCode не использует файлы `mcp.json` или `settings.json` для конфигурации MCP серверов.

**Решение:** Используйте CLI инструмент Claude Code для добавления серверов.

## 🛠️ Быстрый старт

### 1. Использование helper скрипта (рекомендуется)

```cmd
# Показать все серверы
add-mcp-server.bat list

# Добавить новый сервер
add-mcp-server.bat add имя_сервера -- npx -y package-name

# Удалить сервер
add-mcp-server.bat remove имя_сервера

# Информация о сервере
add-mcp-server.bat get имя_сервера
```

### 2. Прямое использование CLI

```cmd
# Путь к CLI
set CLAUDE_CLI=C:\Users\Shtim\.vscode\extensions\anthropic.claude-code-2.0.15\resources\claude-code\cli.js

# Добавить сервер
node "%CLAUDE_CLI%" mcp add --scope user --transport stdio server-name -- npx -y package-name

# Список серверов
node "%CLAUDE_CLI%" mcp list

# Удалить сервер
node "%CLAUDE_CLI%" mcp remove --scope user server-name
```

## 📋 Примеры добавления популярных MCP серверов

### 1. Filesystem (доступ к файлам)
```cmd
add-mcp-server.bat add filesystem -- npx @modelcontextprotocol/server-filesystem "E:\Shtim\Downloads"
```

### 2. Sequential Thinking (пошаговое мышление)
```cmd
add-mcp-server.bat add sequential-thinking -- npx @modelcontextprotocol/server-sequential-thinking
```

### 3. Chrome DevTools (отладка браузера)
```cmd
add-mcp-server.bat add chrome-devtools -- npx -y chrome-devtools-mcp@latest
```

### 4. Brave Search (веб-поиск)
```cmd
add-mcp-server.bat add brave-search -- npx -y @modelcontextprotocol/server-brave-search
```

### 5. Git (интеграция с Git)
```cmd
add-mcp-server.bat add git -- npx -y @modelcontextprotocol/server-git
```

### 6. GitHub (интеграция с GitHub)
```cmd
add-mcp-server.bat add github -- npx -y @modelcontextprotocol/server-github
```

### 7. PostgreSQL (подключение к БД)
```cmd
add-mcp-server.bat add postgres -- npx -y @modelcontextprotocol/server-postgres
```

### 8. Slack (интеграция со Slack)
```cmd
add-mcp-server.bat add slack -- npx -y @modelcontextprotocol/server-slack
```

### 9. Time (работа со временем)
```cmd
add-mcp-server.bat add mcp-server-time -- python -m mcp_server_time --local-timezone=Europe/Tallinn
```

### 10. HTTP сервер (например, Sentry)
```cmd
node "%CLAUDE_CLI%" mcp add --scope user --transport http sentry https://mcp.sentry.dev/mcp
```

## 🔧 Три типа транспорта

### 1. **stdio** (самый распространенный)
Для серверов, запускаемых как процесс (npx, python, node)
```cmd
--transport stdio
```

### 2. **http**
Для HTTP API серверов
```cmd
--transport http
```

### 3. **sse** (Server-Sent Events)
Для SSE потоков
```cmd
--transport sse
```

## 📂 Три уровня scope

### 1. **user** (рекомендуется) ✅
Серверы доступны во всех проектах пользователя
```cmd
--scope user
```

### 2. **local**
Серверы только для текущей директории
```cmd
--scope local
```

### 3. **project**
Серверы для текущего VSCode workspace
```cmd
--scope project
```

## 🌍 Переменные окружения

Добавление серверов с переменными окружения (API ключи, токены):

```cmd
node "%CLAUDE_CLI%" mcp add --scope user --transport stdio server-name --env API_KEY=your_key_here --env TOKEN=your_token -- npx -y package-name
```

Пример с Brave Search:
```cmd
node "%CLAUDE_CLI%" mcp add --scope user --transport stdio brave-search --env BRAVE_API_KEY=your_api_key -- npx -y @modelcontextprotocol/server-brave-search
```

## 🔍 Поиск новых MCP серверов

### Официальный репозиторий MCP серверов:
- GitHub: https://github.com/modelcontextprotocol/servers
- NPM: поиск по `mcp-server` или `@modelcontextprotocol/server-*`

### Популярные источники:
- Model Context Protocol Registry: https://mcp-registry.org/
- Awesome MCP Servers: https://github.com/punkpeye/awesome-mcp-servers

## ❓ В чем была проблема?

### 🔴 Что НЕ работает для Claude Code в VSCode:

1. ❌ **claude_desktop_config.json** (только для Claude Desktop приложения)
2. ❌ **mcp.json** в VSCode User папке (для GitHub Copilot)
3. ❌ **settings.json** с `claude-code.mcpServers` (не поддерживается)

### ✅ Что работает:

**Только CLI** с сохранением в `.claude.json`:
```
C:\Users\Shtim\.claude.json
```

## 🤔 Почему так сложно?

### Причины:

1. **Разные продукты = разные конфигурации**
   - Claude Desktop (Electron) → свой формат
   - Claude Code VSCode (расширение) → свой формат через CLI
   - GitHub Copilot → свой формат

2. **Документация не очевидна**
   - В UI показывается "use claude mcp add", но не объясняется как

3. **Windows особенности**
   - Пути с `\` требуют экранирования в JSON
   - WSL + Windows пути добавляют путаницу

4. **Архитектура Claude Code**
   - Расширение хранит конфигурацию отдельно от VSCode settings
   - CLI единственный официальный способ управления

## 🚨 Важные замечания

### ⚠️ Версия расширения в пути

Путь к CLI содержит версию расширения:
```
anthropic.claude-code-2.0.15
```

При обновлении расширения номер версии изменится! В таком случае:

1. Найдите новую версию:
```cmd
code --locate-extension anthropic.claude-code
```

2. Обновите `CLAUDE_CLI` в `add-mcp-server.bat`

### 💡 Альтернатива (универсальный путь)

Создайте alias или переменную окружения:
```cmd
# В Windows Environment Variables добавьте:
CLAUDE_CLI=C:\Users\%USERNAME%\.vscode\extensions\anthropic.claude-code-*\resources\claude-code\cli.js
```

## 📊 Проверка статуса серверов

### Показать все серверы с их статусом:
```cmd
add-mcp-server.bat list
```

Вывод покажет:
- ✓ Connected - сервер работает
- ✗ Failed to connect - проблема с подключением

### Детальная информация о сервере:
```cmd
add-mcp-server.bat get server-name
```

## 🔄 Обновление MCP серверов

MCP серверы, установленные через npx с флагом `-y`, автоматически используют последнюю версию при каждом запуске.

Для принудительного обновления кеша npx:
```cmd
npx clear-npx-cache
```

## 📝 Файл конфигурации

Все MCP серверы сохраняются в:
```
C:\Users\Shtim\.claude.json
```

Структура (для справки, **НЕ редактируйте вручную!**):
```json
{
  "user": {
    "mcpServers": {
      "server-name": {
        "type": "stdio",
        "command": "npx",
        "args": ["-y", "package-name"],
        "env": {}
      }
    }
  }
}
```

## 🎓 Итоговый workflow

### Добавление нового MCP сервера:

1. **Найдите MCP сервер** (GitHub, NPM, MCP Registry)
2. **Используйте helper скрипт**:
   ```cmd
   add-mcp-server.bat add server-name -- npx -y package-name
   ```
3. **Проверьте статус**:
   ```cmd
   add-mcp-server.bat list
   ```
4. **Готово!** Сервер сразу доступен в Claude Code (без перезапуска VSCode)

## 🆘 Troubleshooting

### Проблема: "No MCP servers configured"

**Решение:** Убедитесь, что используете `--scope user`, а не `--scope local`:
```cmd
node "%CLAUDE_CLI%" mcp add --scope user --transport stdio server-name -- command
```

### Проблема: "Command not found" или сервер не запускается

**Проверьте:**
1. Установлен ли Node.js и доступен ли npx
2. Для Python серверов - установлен ли Python и нужный пакет
3. Правильность команды запуска

**Тестирование команды вручную:**
```cmd
npx -y package-name
```

### Проблема: Сервер показывает "✗ Failed to connect"

**Возможные причины:**
1. Неправильная команда запуска
2. Отсутствуют зависимости (Node.js, Python, etc.)
3. Требуются переменные окружения (API ключи)
4. Проблема с самим MCP пакетом

**Решение:** Проверьте детали ошибки в Output панели VSCode (Claude Code)

### Проблема: Не могу найти CLI после обновления расширения

**Решение:**
```cmd
code --locate-extension anthropic.claude-code
```
Обновите путь в `add-mcp-server.bat`

## 📚 Полезные ссылки

- **Model Context Protocol Docs:** https://modelcontextprotocol.io/
- **Claude Code Docs:** https://docs.claude.com/claude-code
- **MCP Servers Registry:** https://mcp-registry.org/
- **Official MCP Servers:** https://github.com/modelcontextprotocol/servers
- **Awesome MCP:** https://github.com/punkpeye/awesome-mcp-servers

---

**Последнее обновление:** 2025-10-15
**Версия Claude Code:** 2.0.15
**Автор:** Claude Code Assistant
