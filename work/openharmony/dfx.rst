openHarmony DFX总结
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

应用恢复API全集
==================================

.. list-table:: 应用恢复API全集
    :header-rows: 1

    * - 接口
      - 说明

    * - ohos.application.appRecovery.saveAppState()
      - 主动保存Ability状态

    * - ohos.application.appRecovery.restartApp()
      - 主动重启应用

    * - ohos.application.Ability.onSaveState(reason,wantParam )
      - 框架回调保存Ability状态

    * - Ohos.appRecovery.enableAppRecovery(restartFlag,eSaveOccasionFlag, SaveModeFlag)
      - 使能自动保存恢复应用

    * - ohos.application.appRecovery.restartFlag
      - 重启的选项,包括: 不限制重启场景 应用卡死时不重启；应用NativeCrash时不重启；应用JsError时不重启

    * - ohos.application.appRecovery.SaveOccasionFlag
      - 持久化状态时机的选项,包括:不自动保存 应用故障时保存；应用在onBackground时保存

    * - ohos.application.appRecovery.SaveModeFlag
      - 持久化状态方式的选择,包括： 使用文件持久化；使用数据库持久化；使用共享内存持久化