Item Scroller
==============
Item Scroller is a Minecraft mod that adds various convenience features for moving items
inside inventory GUIs. Examples are scrolling the mouse wheel over slots with items in them
or Shift/Ctrl + click + dragging over slots to move items from them in various ways etc.

Item scrolling is basically what the old NEI mod did and Mouse Tweaks also does.
This mod has some different drag features compared to Mouse Tweaks, and also some special
villager trading related helper features as well as crafting helper features.

For more information and downloads of the already compiled builds,
see https://www.curseforge.com/minecraft/mc-mods/item-scroller

## MRQ 修复

本分支基于上游代码进行了以下 bug 修复：

### 严重修复
- **村民交易索引错误**: `villagerTradeEverythingPossibleWithAllFavoritedTrades()` 中循环使用 `favorites.getInt(i)` 获取实际交易索引，修复用循环计数器直接当交易索引的 bug
- **I/O 资源泄漏**: `RecipeStorage` 和 `VillagerDataStorage` 中 FileInputStream/FileOutputStream 改为 try-with-resources
- **拖拽状态清理**: `stopDragging()` 增加重置 `lastPosX`/`lastPosY`/`slotNumberLast`，防止下次拖拽从错误位置开始

### 安全修复
- `RecipePattern.readFromNBT()`: NBT Length 添加上限 9，防止损坏文件导致 OOM

### 构建修复
- `build.gradle`: Loom 版本 1.4→1.2，移除已废弃的 `sourceSourceSets` 配置

Compiling
=========
* Clone the repository
* Open a command prompt/terminal to the repository directory
* run 'gradlew build'
* The built jar file will be in build/libs/