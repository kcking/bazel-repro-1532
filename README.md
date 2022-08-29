reproduction for https://github.com/bazelbuild/rules_rust/pull/1532

running `bazel build //:wasm-and-bin`

results in
```
Analyzing: target //:wasm-and-bin (196 packages loaded, 8245 targets configured)
FATAL: bazel crashed due to an internal error. Printing stack trace:
java.lang.RuntimeException: Unrecoverable error while evaluating node 'ConfiguredTargetKey{label=@bazel_tools//tools/cpp:current_cc_toolchain, config=BuildConfigurationValue.Key[92e5d91b302bd50add78c487b06a677a8c261db39969e92317ccc69c68cd948e]}' (requested by nodes 'ConfiguredTargetKey{label=//:bin, config=BuildConfigurationValue.Key[92e5d91b302bd50add78c487b06a677a8c261db39969e92317ccc69c68cd948e]}', 'ToolchainDependencyConfiguredTargetKey{label=@rust_darwin_aarch64__wasm32-unknown-unknown_tools//:rust_toolchain, config=BuildConfigurationValue.Key[92e5d91b302bd50add78c487b06a677a8c261db39969e92317ccc69c68cd948e], executionPlatformLabel=@local_config_platform//:host}')
        at com.google.devtools.build.skyframe.AbstractParallelEvaluator$Evaluate.run(AbstractParallelEvaluator.java:674)
        at com.google.devtools.build.lib.concurrent.AbstractQueueVisitor$WrappedRunnable.run(AbstractQueueVisitor.java:382)
        at java.base/java.util.concurrent.ForkJoinTask$RunnableExecuteAction.exec(ForkJoinTask.java:1426)
        at java.base/java.util.concurrent.ForkJoinTask.doExec(ForkJoinTask.java:290)
        at java.base/java.util.concurrent.ForkJoinPool$WorkQueue.topLevelExec(ForkJoinPool.java:1020)
        at java.base/java.util.concurrent.ForkJoinPool.scan(ForkJoinPool.java:1656)
        at java.base/java.util.concurrent.ForkJoinPool.runWorker(ForkJoinPool.java:1594)
        at java.base/java.util.concurrent.ForkJoinWorkerThread.run(ForkJoinWorkerThread.java:183)
Caused by: java.lang.NullPointerException
        at com.google.devtools.build.lib.rules.cpp.CcToolchain.createMakeVariableProvider(CcToolchain.java:122)
        at com.google.devtools.build.lib.rules.cpp.CcToolchainAliasRule$CcToolchainAlias.create(CcToolchainAliasRule.java:78)
        at com.google.devtools.build.lib.rules.cpp.CcToolchainAliasRule$CcToolchainAlias.create(CcToolchainAliasRule.java:69)
        at com.google.devtools.build.lib.analysis.ConfiguredTargetFactory.createRule(ConfiguredTargetFactory.java:364)
        at com.google.devtools.build.lib.analysis.ConfiguredTargetFactory.createConfiguredTarget(ConfiguredTargetFactory.java:188)
        at com.google.devtools.build.lib.skyframe.SkyframeBuildView.createConfiguredTarget(SkyframeBuildView.java:1108)
        at com.google.devtools.build.lib.skyframe.ConfiguredTargetFunction.createConfiguredTarget(ConfiguredTargetFunction.java:980)
        at com.google.devtools.build.lib.skyframe.ConfiguredTargetFunction.compute(ConfiguredTargetFunction.java:368)
        at com.google.devtools.build.skyframe.AbstractParallelEvaluator$Evaluate.run(AbstractParallelEvaluator.java:590)
        ... 7 more
```
