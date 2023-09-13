---

title: 重置GitLab pull mirror功能
tag: GitLab
---

  


网络出现一段问题，导致 `gitlab` 的 `pull mirror` 功能超过了 `最大重试次数`，进入了暂停 pull mirror 的状态。重置多个项目的 `pull mirror` 功能，如下：

  

## 进入 `gitlab-rails console`


> $ docker exec -it gitlab bash
> $ gitlab-rails console

  


执行以下命令


```bash

Project.find_each do |p|

  if p.import_state && p.import_state.retry_count >= 14

    puts "Resetting mirroring operation for #{p.full_path}"

    p.import_state.reset_retry_count

    p.import_state.set_next_execution_to_now(prioritized: true)

  p.import_state.save!

end

end

```



> Written with [StackEdit](https:stackedit.io/)---
title: 重置GitLab pull mirror功能tag: GitLab---  网络出现一段问题，导致 `gitlab` 的 `pull mirror` 功能超过了 `最大重试次数`，进入了暂停 pull mirror 的状态。重置多个项目的 `pull mirror` 功能，如下：  ## 进入 `gitlab-rails console`> $ docker exec -it gitlab bash> $ gitlab-rails console  执行以下命令```bashProject.find_each do |p|  if p.import_state && p.import_state.retry_count >= 14    puts "Resetting mirroring operation for #{p.full_path}"    p.import_state.reset_retry_count    p.import_state.set_next_execution_to_now(prioritized: true)  p.import_state.save!endend```> Written with [StackEdit](https:stackedit.io/)
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTEwMDY0NTI5MDBdfQ==
-->