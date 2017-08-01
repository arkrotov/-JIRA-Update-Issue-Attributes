# 1. Открываем консоль (нужна админка)
--------------------------------------
```sh
http://jira.eldorado.ru/plugins/servlet/scriptrunner/console?section=script_console
```

# 2. Вставляем следующий код.
---------------------------
```sh
import com.atlassian.jira.component.ComponentAccessor;
import com.atlassian.jira.issue.MutableIssue;
import java.sql.Timestamp;

MutableIssue issue = ComponentAccessor.getIssueManager().getIssueByCurrentKey("Test-111"); // Номер задачи
issue.setResolutionObject(getConstantsManager().getResolutionObject("1")); // Резолюция (возможно: null)
issue.setOriginalEstimate((long) (32*60*60)); // Оценка
issue.setTimeSpent((long) 24*60*60); // Затрачено
issue.setEstimate((long) 8*60*60); // Осталось
issue.setCreated(new Timestamp(117,5,26,8,0,0,0)); // Дата создания (год - 1900/месяц - 1/день/часы/минуты/секунды/наносекунды)
issue.setUpdated(new Timestamp(117,5,26,8,0,0,0)); // Дата обновления (год - 1900/месяц - 1/день/часы/минуты/секунды/наносекунды)
issue.setAssignee(ComponentAccessor.getUserUtil().getUserByName("akrotov").getDirectoryUser()); // Устанавливаем исполнителя
issue.setReporter(ComponentAccessor.getUserUtil().getUserByName("akrotov").getDirectoryUser()); // Устанавливаем автора
ComponentAccessor.getChangeHistoryManager().removeAllChangeItems(issuee); // Удалить историю
issue.store(); // Применить изменения
```

# 3. Изменяем, что нужно и жмем run. (действия которые вам не нужны, можно удалить)
# 4. Solved!


