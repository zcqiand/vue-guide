# SAGA II是什么？
SAGA II是最早的计算机生成叙事之一，该程序可以在简单的剧本中生成无限数量的变体。由麻省理工学院（MIT）的Douglas T. Ross和Harrison R. Morse创建，并出现在1962年由哥伦比亚广播公司（CBS）和麻省理工学院（MIT）共同制作的电视特辑The Thinking Machine中。

SAGA II的故事有两个角色：一个是强盗，另一个是警长。角色表现出鲜明的人格特质：强盗经常饮酒并试图藏钱；如果警长看见强盗，就会向强盗开枪。

与现代角色扮演游戏一样，每个角色在死亡之前都会遭受一定程度的伤害，并且角色行为会因伤害而改变。最终，其中一个角色被杀死，另一个角色是胜利者。

# SAGA II实现细节
每个演员的手都被单独表示，并且有一个简单的容器和支持者世界模型。

在每个时间步骤中，参与者都会“主动行动”（就像现代RPG中一样），以确定谁执行动作。因为强盗首先出现在现场，所以警长的主动性在最初的时间步长被硬编码为零。

当演员赢得主动权时，程序将为演员选择动作。每个参与者都维护一个队列，该队列将要执行的下一个动作可能是零长度。如果队列中有操作，则立即执行；否则，将立即执行该操作。如果没有行动排队，行动者将从一系列加权行动中进行选择：喝酒，搬到新地点等。某些行动将花费多个时间，例如“藏钱”；采取该操作时，它将把所有与其相关的操作推入队列。

强盗和警长的特定情况对每种行为都有不同的权重。强盗将试图藏​​钱。警长将在他的第一个回合直接移动到房屋中。行动的结果受故事状态的影响。如果他受伤，警长有更好的目标。

成绩单样本

      SAGA III An Original Play by a Computer
      Act 1 Scene 1
      
      The holster is on the robber. The sheriff's gun is in the sheriff's right hand.
      The sheriff's holster is on the sheriff. The glass is on the table.
      The bottle is on the table. The gun is in the robber's right hand.
      The money is in the robber's left hand.
      
      ROBBER
      (The robber is at the window.)
      open door
      go through door
      close door
      go to corner
      put money on corner
      go to table
      pick up the glass with the robber's left hand
      put glass on table
      pick up the bottle with the robber's left hand
      put gun on table
      pour
      pick up the glass with the robber's right hand
      take a drink from glass
      take a drink from glass
      take a drink from glass
      put glass on table
      go to window
      put bottle on window
      go to corner
      
      SHERIFF
      go to window
      open door
      go through door
      
      ROBBER
      go to table
      
      SHERIFF
      close door
      aim
      fire
      robber HIT
      
      ROBBER
      pick up the gun with the robber's right hand
      aim
      fire
      sheriff HIT
      
      SHERIFF
      aim
      
      ROBBER
      aim
      fire
      MISSED
      aim
      fire
      sheriff NICKED
      
      SHERIFF
      fire
      MISSED
      
      ROBBER
      aim
      
      SHERIFF
      fire
      robber NICKED
      fire
      robber NICKED
      fire
      MISSED
      
      ROBBER
      fire
      sheriff NICKED
      fire
      sheriff HIT
      
      SHERIFF
      sheriff dies.
      
      ROBBER
      blow out barrel
      put gun in holster
      pick up the glass with the robber's right hand
      go to corner
      pick up the money with the robber's left hand
      open door
      
      CURTAIN
      

# 资源

* [《SAGA II初步操作说明》](http://bitsavers.trailing-edge.com/pdf/mit/tx-0/memos/Morse_SAGAII_Oct60.pdf)