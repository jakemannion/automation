```mermaid
    graph TD
   t1["Recurrence"]
   s2["init_assignmentArray"]
   s3["init_taskObject"]
   s4["init_errorString"]
   s5["init_taskArray"]
   s6["init_checklistArray"]
   s7["init_labelArray"]
   s8["init_attachmentArray"]
   s9["init_labelValuesArray<p style='font-size:x-small; height:fit-content; word-wrap:break-word;' title='used for storing the label info for a given plan - dont think it&#039;s used'>used for storing the label info for a given plan - dont think it&#039;s used</p>"]
   s10["Plan_and_task_iteration"]
   s11["for_each_plan"]
   s12["List_buckets"]
   s13["List_tasks"]
   s14["for_each_task"]
   s15["filter_bucket_array"]
   s16["is_more_task_detail_needed<p style='font-size:x-small; height:fit-content; word-wrap:break-word;' title='if a task has no description, checklist, or attachments, we don&#039;t need to run &#039;Get task details&#039;'>if a task has no description, checklist, or attachments, we don&#039;t need to run &#039;Get task details&#039;</p>"]
   s17["Get_task_details"]
   s18["for_each_checklist_item"]
   s19["append_to_checklist_array"]
   s20["for_each_attachment"]
   s21["append_to_attachmentArray"]
   s22["append_taskObject_to_taskArray_detailed"]
   s23["else"]
   s24["append_taskObject_to_taskArray"]
   s25["for_each_assignment"]
   s26["append_to_assignmentArray"]
   s27["task_labels_object"]
   s28["Parse_JSON_for_task_labels"]
   s29["task_labels_array"]
   s30["for_each_task_label"]
   s31["filter_plan_labels_with_task_labels"]
   s32["append_to_labelArray"]
   s33["filter_task_labels_array"]
   s34["if_label_25_support_is_true"]
   s35["if_task_not_complete"]
   s36["link_to_this_task"]
   s37["Post_message_in_a_chat_or_channel"]
   s38["log_help_request"]
   s39["plan_label_values_array"]
   s40["Get_plan_details"]
   s41["Append_to_errorString_2<p style='font-size:x-small; height:fit-content; word-wrap:break-word;' title='if service account does not have plan access, an error will generate'>if service account does not have plan access, an error will generate</p>"]
   s42["increment_errorCount_2"]
   s43["update_lastRunDate_on_source_row"]
   s44["get_active_plans<p style='font-size:x-small; height:fit-content; word-wrap:break-word;' title='get active plans from SQL table (populated and managed by customer via powerApp)'>get active plans from SQL table (populated and managed by customer via powerApp)</p>"]
   s45["increment_errorCount"]
   s46["append_errorString"]
   s47["check_for_email_notification_preference"]
   s48["send_completion_email_lite"]
   s49["init_errorCount"]
   s50["Start_time_PST"]
   s51["get_existing_SQL_records"]
   s52["get_existing_tasks"]
   s53["get_existing_assignments"]
   s54["get_existing_attachments"]
   s55["get_existing_checklist_items"]
   s56["get_existing_labels"]
   s57["init_recordCounts"]
   s58["init_outcomeArray"]
   s59["init_inactiveTasks_array"]
   s60["init_inactiveLabels_array"]
   s61["init_inactiveAttachments_array"]
   s62["init_inactiveAssignments_array"]
   s63["init_inactiveChecklist_array"]
   s64["HTTP"]
   s65["http_response"]
   s66["End_Time_PST"]
   s67["compose_totals"]
   s68["array_payloads"]
   s69["log_outcome"]
   s70["if_weekday"]
   s71["Terminate"]
   subgraph g1["Plan_and_task_iteration (Scope)"]
   s10
   s72["/Plan_and_task_iteration"]
   s11
   s44
   s45
   s46
   subgraph g2["for_each_plan (Foreach)"]
   s11
   s73["/for_each_plan"]
   s12
   s13
   s14
   s39
   s40
   s41
   s42
   s43
   subgraph g3["for_each_task (Foreach)"]
   s14
   s74["/for_each_task"]
   s15
   s16
   s25
   s27
   s28
   s29
   s30
   s33
   s34
   subgraph g4["is_more_task_detail_needed (If)"]
   s16
   s75["/is_more_task_detail_needed"]
   s17
   s18
   s20
   s22
   subgraph g5["for_each_checklist_item (Foreach)"]
   s18
   s76["/for_each_checklist_item"]
   s19
   s19 --> s76
%% /for_each_checklist_item
   end
   subgraph g6["for_each_attachment (Foreach)"]
   s20
   s77["/for_each_attachment"]
   s21
   s21 --> s77
%% /for_each_attachment
   end
   s22 --> s75
%% /is_more_task_detail_needed
   end
   subgraph g7["for_each_assignment (Foreach)"]
   s25
   s78["/for_each_assignment"]
   s26
   s26 --> s78
%% /for_each_assignment
   end
   subgraph g8["for_each_task_label (Foreach)"]
   s30
   s79["/for_each_task_label"]
   s31
   s32
   s32 --> s79
%% /for_each_task_label
   end
   subgraph g9["if_label_25_support_is_true (If)"]
   s34
   s80["/if_label_25_support_is_true"]
   s35
   subgraph g10["if_task_not_complete (If)"]
   s35
   s81["/if_task_not_complete"]
   s36
   s37
   s38
   s38 --> s81
%% /if_task_not_complete
   end
   s81 --> s80
%% /if_label_25_support_is_true
   end
   s80 --> s74
%% /for_each_task
   end
   s43 --> s73
%% /for_each_plan
   end
   s46 --> s72
%% /Plan_and_task_iteration
   end
   subgraph g11["check_for_email_notification_preference (If)"]
   s47
   s82["/check_for_email_notification_preference"]
   s48
   s48 --> s82
%% /check_for_email_notification_preference
   end
   subgraph g12["get_existing_SQL_records (Scope)"]
   s51
   s83["/get_existing_SQL_records"]
   s52
   s53
   s54
   s55
   s56
   s56 --> s83
%% /get_existing_SQL_records
   end
   subgraph g13["if_weekday (If)"]
   s70
   s84["/if_weekday"]
%% /if_weekday
   end
   s5 --> s2
   s49 --> s3
   s58 --> s4
   s3 --> s5
   s7 --> s6
   s9 --> s7
   s2 --> s8
   s8 --> s9
   s57 --> s10
   s44 --> s11
   s11 --> s12
   s39 --> s13
   s13 --> s14
   s14 --> s15
   s15 --> s16
   s16 --> s17
   s22 --> s18
   s18 --> s19
   s76 --> s20
   s20 --> s21
   s17 --> s22
   s16 --Else--> s24
   s75 --> s25
   s25 --> s26
   s78 --> s27
   s27 --> s28
   s28 --> s29
   s33 --> s30
   s30 --> s31
   s31 --> s32
   s29 --> s33
   s79 --> s34
   s34 --> s35
   s35 --> s36
   s36 --> s37
   s37 --> s38
   s40 --> s39
   s12 --> s40
   s12 -.Failed.-> s41
   s41 --> s42
   s74 --> s43
   s10 --> s44
   s44 -.Failed,TimedOut.-> s45
   s45 --> s46
   s65 -.TimedOut.-> s47
   s47 --> s48
   s4 --> s49
   t1 --> s50
   s6 --> s51
   s51 --> s52
   s52 --> s53
   s53 --> s54
   s54 --> s55
   s55 --> s56
   s83 --> s57
   s63 --> s58
   s84 --> s59
   s62 --> s60
   s59 --> s61
   s61 --> s62
   s60 --> s63
   s68 --> s64
   s64 --> s65
   s72 -.Succeeded,Failed.-> s66
   s66 --> s67
   s67 --> s68
   s65 --> s69
   s50 --> s70
   s70 --Else--> s71
```
