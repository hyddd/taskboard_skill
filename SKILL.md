<skill>
  <name>taskboard</name>
  <description>Manage tasks, project status, and todo lists using the TaskBoardAI Kanban system. Use this whenever the user mentions "【任务】", asks to check task status, or when a complex plan needs to be broken down into tracked items. Supports creating tasks, moving columns (todo/doing/done), and adding subtasks. NOTE: The main body of the card must be stored in the 'content' field, not 'description'.</description>
  <mcp_server>
    <command>node</command>
    <args>
      <arg>/opt/homebrew/lib/node_modules/taskboardai/server/mcp/kanbanMcpServer.js</arg>
    </args>
  </mcp_server>
</skill>
