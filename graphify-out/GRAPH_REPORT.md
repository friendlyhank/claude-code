# Graph Report - claude-code  (2026-04-25)

## Corpus Check
- 2926 files · ~3,658,145 words
- Verdict: corpus is large enough that graph structure adds value.

## Summary
- 12411 nodes · 38767 edges · 44 communities detected
- Extraction: 67% EXTRACTED · 33% INFERRED · 0% AMBIGUOUS · INFERRED: 12924 edges (avg confidence: 0.8)
- Token cost: 0 input · 0 output

## Community Hubs (Navigation)
- [[_COMMUNITY_Community 0|Community 0]]
- [[_COMMUNITY_Community 1|Community 1]]
- [[_COMMUNITY_Community 2|Community 2]]
- [[_COMMUNITY_Community 3|Community 3]]
- [[_COMMUNITY_Community 4|Community 4]]
- [[_COMMUNITY_Community 5|Community 5]]
- [[_COMMUNITY_Community 6|Community 6]]
- [[_COMMUNITY_Community 7|Community 7]]
- [[_COMMUNITY_Community 8|Community 8]]
- [[_COMMUNITY_Community 9|Community 9]]
- [[_COMMUNITY_Community 10|Community 10]]
- [[_COMMUNITY_Community 11|Community 11]]
- [[_COMMUNITY_Community 12|Community 12]]
- [[_COMMUNITY_Community 13|Community 13]]
- [[_COMMUNITY_Community 14|Community 14]]
- [[_COMMUNITY_Community 15|Community 15]]
- [[_COMMUNITY_Community 16|Community 16]]
- [[_COMMUNITY_Community 17|Community 17]]
- [[_COMMUNITY_Community 18|Community 18]]
- [[_COMMUNITY_Community 19|Community 19]]
- [[_COMMUNITY_Community 20|Community 20]]
- [[_COMMUNITY_Community 21|Community 21]]
- [[_COMMUNITY_Community 22|Community 22]]
- [[_COMMUNITY_Community 23|Community 23]]
- [[_COMMUNITY_Community 24|Community 24]]
- [[_COMMUNITY_Community 25|Community 25]]
- [[_COMMUNITY_Community 26|Community 26]]
- [[_COMMUNITY_Community 27|Community 27]]
- [[_COMMUNITY_Community 28|Community 28]]
- [[_COMMUNITY_Community 29|Community 29]]
- [[_COMMUNITY_Community 30|Community 30]]
- [[_COMMUNITY_Community 31|Community 31]]
- [[_COMMUNITY_Community 32|Community 32]]
- [[_COMMUNITY_Community 33|Community 33]]
- [[_COMMUNITY_Community 34|Community 34]]
- [[_COMMUNITY_Community 35|Community 35]]
- [[_COMMUNITY_Community 36|Community 36]]
- [[_COMMUNITY_Community 37|Community 37]]
- [[_COMMUNITY_Community 38|Community 38]]
- [[_COMMUNITY_Community 40|Community 40]]
- [[_COMMUNITY_Community 42|Community 42]]
- [[_COMMUNITY_Community 43|Community 43]]
- [[_COMMUNITY_Community 44|Community 44]]
- [[_COMMUNITY_Community 50|Community 50]]

## God Nodes (most connected - your core abstractions)
1. `logForDebugging()` - 797 edges
2. `logError()` - 341 edges
3. `logEvent()` - 341 edges
4. `jsonStringify()` - 197 edges
5. `errorMessage()` - 184 edges
6. `isEnvTruthy()` - 171 edges
7. `getFsImplementation()` - 165 edges
8. `getGlobalConfig()` - 139 edges
9. `getCwd()` - 112 edges
10. `getFeatureValue_CACHED_MAY_BE_STALE()` - 110 edges

## Surprising Connections (you probably didn't know these)
- `createTestProgram()` --calls--> `description()`  [INFERRED]
  tests/integration/cli-arguments.test.ts → src/commands/model/index.ts
- `downloadUrlToBufferWithFallback()` --calls--> `readFileSync()`  [INFERRED]
  scripts/download-ripgrep.ts → src/utils/fileRead.ts
- `downloadAndExtract()` --calls--> `log()`  [INFERRED]
  scripts/download-ripgrep.ts → src/utils/claudeInChrome/chromeNativeHost.ts
- `downloadAndExtract()` --calls--> `round()`  [INFERRED]
  scripts/download-ripgrep.ts → src/cost-tracker.ts
- `exec()` --calls--> `open()`  [INFERRED]
  src/utils/Shell.ts → packages/@ant/computer-use-swift/src/index.ts

## Communities

### Community 0 - "Community 0"
Cohesion: 0.0
Nodes (413): call(), getSubagentLogName(), isSubagentContext(), extractTranscript(), logContainsQuery(), call(), createApiQueryHook(), uniq() (+405 more)

### Community 1 - "Community 1"
Cohesion: 0.01
Nodes (937): getAddDirEnabledPlugins(), getAddDirExtraMarketplaces(), handleAdd(), checkAdminRequestEligibility(), createAdminRequest(), getMyAdminRequests(), agenticSessionSearch(), axiosGetWithRetry() (+929 more)

### Community 2 - "Community 2"
Cohesion: 0.01
Nodes (375): getSettingsWithAllErrors(), parseArgumentNames(), parseArguments(), substituteArguments(), InvalidApiKeyMessage(), checkGcpCredentialsValid(), GcpCredentialsTimeoutError, getConfiguredAwsAuthRefresh() (+367 more)

### Community 3 - "Community 3"
Cohesion: 0.0
Nodes (494): App(), handleMouseEvent(), processKeysInBatch(), resumeHandler(), memoryHeader(), authLogout(), getBidi(), hasRTLCharacters() (+486 more)

### Community 4 - "Community 4"
Cohesion: 0.01
Nodes (564): ActivityManager, getAgentColor(), setAgentColor(), isTeammateAgentContext(), getOverrideSourceLabel(), resolveAgentOverrides(), agentsHandler(), formatAgent() (+556 more)

### Community 5 - "Community 5"
Cohesion: 0.01
Nodes (454): authLogin(), authStatus(), calculateApiKeyHelperTTL(), getAnthropicApiKey(), getAnthropicApiKeyWithSource(), getApiKeyFromApiKeyHelper(), getApiKeyFromApiKeyHelperCached(), getAuthTokenSource() (+446 more)

### Community 6 - "Community 6"
Cohesion: 0.01
Nodes (373): createAbortController(), createChildAbortController(), optionForPermissionSaveDestination(), runWithAgentContext(), getSessionMessages(), query(), getRecordFilePath(), getSessionRecordingPaths() (+365 more)

### Community 7 - "Community 7"
Cohesion: 0.01
Nodes (360): call(), canUserConfigureAdvisor(), getAdvisorConfig(), getExperimentAdvisorModels(), getInitialAdvisorSetting(), isAdvisorEnabled(), isValidAdvisorModel(), modelSupportsAdvisor() (+352 more)

### Community 8 - "Community 8"
Cohesion: 0.01
Nodes (282): registerMcpAddCommand(), clearAllAsyncHooks(), finalizeHook(), finalizePendingAsyncHooks(), getDirectoriesToProcess(), getDynamicSkillAttachments(), getNestedMemoryAttachments(), getNestedMemoryAttachmentsForFile() (+274 more)

### Community 9 - "Community 9"
Cohesion: 0.01
Nodes (359): countToolUses(), emitTaskProgress(), extractPartialResult(), finalizeAgentTool(), getLastToolUseName(), runAsyncAgentLifecycle(), normalizeToolInput(), prependUserContext() (+351 more)

### Community 10 - "Community 10"
Cohesion: 0.01
Nodes (274): resolveAttachments(), validateAttachmentPaths(), bashToolCheckCommandOperatorPermissions(), buildSegmentWithoutRedirections(), checkCommandOperatorPermissions(), detectBlockedSleepPattern(), isAutobackgroundingAllowed(), isSearchOrReadBashCommand() (+266 more)

### Community 11 - "Community 11"
Cohesion: 0.01
Nodes (250): formatAgentId(), parseAgentId(), getDefaultAppState(), getTaskReminderAttachments(), getTeamContextAttachment(), buildCommandParts(), containsControlStructure(), findFirstPipeOperator() (+242 more)

### Community 12 - "Community 12"
Cohesion: 0.01
Nodes (223): AgentNavigationFooter(), AnimatedAsterisk(), AppStateProvider(), useAppState(), useAppStateStore(), useAppStore(), useSetAppState(), AskUserQuestionPermissionRequest() (+215 more)

### Community 13 - "Community 13"
Cohesion: 0.01
Nodes (170): filterAppsForDescription(), sanitizeAppNames(), sanitizeCore(), sanitizeTrustedNames(), BridgeClient, createBridgeClient(), cleanupComputerUseAfterTurn(), getTerminalBundleId() (+162 more)

### Community 14 - "Community 14"
Cohesion: 0.01
Nodes (226): applySettingsChange(), generateFileAttachment(), getAutoModeExitAttachment(), tryGetPDFReference(), getAutoModeFlagCli(), isAutoModeActive(), isAutoModeCircuitBroken(), setAutoModeActive() (+218 more)

### Community 15 - "Community 15"
Cohesion: 0.01
Nodes (181): getAdvisorUsage(), getDateChangeAttachments(), getMaxBudgetUsdAttachment(), getOutputTokenUsageAttachment(), isGateOpen(), isBriefEntitled(), initialize(), ChannelsNotice() (+173 more)

### Community 16 - "Community 16"
Cohesion: 0.02
Nodes (195): consumeInvokingRequestId(), getAgentContext(), classifyHandoffIfNeeded(), getContextEfficiencyAttachment(), suppressNextSkillListing(), clearApiKeyHelperCache(), clearAwsCredentialsCache(), clearGcpCredentialsCache() (+187 more)

### Community 17 - "Community 17"
Cohesion: 0.02
Nodes (161): backupTerminalPreferences(), checkAndRestoreTerminalBackup(), getTerminalPlistPath(), getTerminalRecoveryInfo(), markTerminalSetupComplete(), markTerminalSetupInProgress(), AskUserQuestionWithHighlight(), openBrowser() (+153 more)

### Community 18 - "Community 18"
Cohesion: 0.02
Nodes (159): getAutoBackgroundMs(), isEnabled(), refreshAwsAuth(), refreshGcpAuth(), shouldSkipVersion(), AwsAuthStatusBox(), AwsAuthStatusManager, truncate() (+151 more)

### Community 19 - "Community 19"
Cohesion: 0.02
Nodes (135): getAgentMemoryDir(), getAgentMemoryEntrypoint(), getLocalAgentMemoryDir(), getMemoryScopeDisplay(), isAgentMemoryPath(), loadAgentMemoryPrompt(), sanitizeAgentTypeForPath(), checkAgentMemorySnapshot() (+127 more)

### Community 20 - "Community 20"
Cohesion: 0.02
Nodes (79): computeShimmerSegments(), CopyPicker(), Cursor, isVimPunctuation(), isVimWhitespace(), isVimWordChar(), MeasuredText, WrappedLine (+71 more)

### Community 21 - "Community 21"
Cohesion: 0.02
Nodes (80): deleteAgentFromFile(), ensureAgentDirectoryExists(), formatAgentAsMarkdown(), getActualAgentFilePath(), getActualRelativeAgentFilePath(), getAgentDirectoryPath(), getNewAgentFilePath(), getNewRelativeAgentFilePath() (+72 more)

### Community 22 - "Community 22"
Cohesion: 0.03
Nodes (108): checkPermissions(), mapToolResultToToolResultBlockParam(), prompt(), requiresUserInteraction(), validateInput(), applyVarToScope(), checkSemantics(), collectCommands() (+100 more)

### Community 23 - "Community 23"
Cohesion: 0.12
Nodes (89): advance(), byteAt(), byteLengthUtf8(), checkBudget(), consumeKeyword(), ensureParserInitialized(), getParserModule(), isArithStop() (+81 more)

### Community 24 - "Community 24"
Cohesion: 0.05
Nodes (59): buildMouseJxa(), captureScreenToBase64(), jxa(), key(), keys(), mouseButton(), mouseLocation(), mouseScroll() (+51 more)

### Community 25 - "Community 25"
Cohesion: 0.05
Nodes (57): AddPermissionRules(), formatContextAsMarkdownTable(), CollapseStatus(), looksLikeISO8601(), parseNaturalLanguageDateTime(), commitTextField(), handleNavigation(), handleTextInputChange() (+49 more)

### Community 26 - "Community 26"
Cohesion: 0.05
Nodes (54): call(), exportWithReactRenderer(), extractFirstPrompt(), formatTimestamp(), sanitizeFilename(), normalizedUpperBound(), renderMessagesToPlainText(), StaticKeybindingProvider() (+46 more)

### Community 27 - "Community 27"
Cohesion: 0.06
Nodes (58): count(), countWorktreeChanges(), executeBYOCPersistence(), executeCloudPersistence(), executeFilePersistence(), isFilePersistenceEnabled(), runFilePersistence(), buildDownloadPath() (+50 more)

### Community 28 - "Community 28"
Cohesion: 0.05
Nodes (44): getDiagnosticAttachments(), callIdeRpc(), DiagnosticTrackingService, escapeForDiff(), getPatchForDisplay(), getPatchFromContents(), addLineNumbers(), convertLeadingTabsToSpaces() (+36 more)

### Community 29 - "Community 29"
Cohesion: 0.04
Nodes (25): AbortError, BoundedUUIDSet, handleIngressMessage(), handleServerControlRequest(), isSDKControlRequest(), isSDKControlResponse(), isSDKMessage(), normalizeControlMessageKeys() (+17 more)

### Community 30 - "Community 30"
Cohesion: 0.04
Nodes (33): deriveSessionTitle(), abbreviateActivity(), truncateToWidth(), formatPastedTextRef(), getPastedTextRefNumLines(), getModeFromInput(), getValueFromInput(), formatTruncatedTextRef() (+25 more)

### Community 31 - "Community 31"
Cohesion: 0.13
Nodes (21): call(), speciesLabel(), companionUserId(), generateSeed(), getCompanion(), hashString(), mulberry32(), pick() (+13 more)

### Community 32 - "Community 32"
Cohesion: 0.11
Nodes (6): clearPendingHint(), extractClaudeCodeHints(), firstCommandToken(), Mailbox, useMailbox(), useMailboxBridge()

### Community 33 - "Community 33"
Cohesion: 0.12
Nodes (4): fromJsonTimestamp(), fromTimestamp(), fromJsonTimestamp(), fromTimestamp()

### Community 34 - "Community 34"
Cohesion: 0.33
Nodes (5): anthropicMessagesToOpenAI(), convertInternalAssistantMessage(), convertInternalUserMessage(), convertToolResult(), systemPromptToText()

### Community 35 - "Community 35"
Cohesion: 0.29
Nodes (1): EndTruncatingAccumulator

### Community 36 - "Community 36"
Cohesion: 0.54
Nodes (7): clickElement(), elementAtPoint(), findElement(), getUITree(), parseJsonSafe(), ps(), setValue()

### Community 37 - "Community 37"
Cohesion: 0.57
Nodes (7): buildGetWindowRectScript(), buildOcrRegionScript(), emptyResult(), ocrRegion(), ocrWindow(), parseOcrOutput(), runPs()

### Community 38 - "Community 38"
Cohesion: 0.33
Nodes (2): createLinkedTransportPair(), InProcessTransport

### Community 40 - "Community 40"
Cohesion: 0.4
Nodes (2): collectEvents(), mockStream()

### Community 42 - "Community 42"
Cohesion: 0.8
Nodes (4): captureWindow(), captureWindowByHwnd(), parseCaptureOutput(), runPs()

### Community 43 - "Community 43"
Cohesion: 0.4
Nodes (2): extractSandboxViolations(), removeSandboxViolationTags()

### Community 44 - "Community 44"
Cohesion: 0.5
Nodes (2): AnimatedClawd(), useClawdAnimation()

### Community 50 - "Community 50"
Cohesion: 0.67
Nodes (2): getModelFamily(), resolveOpenAIModel()

## Knowledge Gaps
- **7 isolated node(s):** `ComputerUseInputAPI`, `MalformedCommandError`, `AutoUpdaterError`, `GcpCredentialsTimeoutError`, `TelemetryTimeoutError` (+2 more)
  These have ≤1 connection - possible missing edges or undocumented components.
- **Thin community `Community 35`** (8 nodes): `EndTruncatingAccumulator`, `.append()`, `.clear()`, `.constructor()`, `.length()`, `.toString()`, `.totalBytes()`, `.truncated()`
  Too small to be a meaningful cluster - may be noise or needs more connections extracted.
- **Thin community `Community 38`** (7 nodes): `createLinkedTransportPair()`, `InProcessTransport`, `.close()`, `.send()`, `._setPeer()`, `.start()`, `InProcessTransport.ts`
  Too small to be a meaningful cluster - may be noise or needs more connections extracted.
- **Thin community `Community 40`** (6 nodes): `streamAdapter.ts`, `streamAdapter.test.ts`, `mapFinishReason()`, `collectEvents()`, `makeChunk()`, `mockStream()`
  Too small to be a meaningful cluster - may be noise or needs more connections extracted.
- **Thin community `Community 43`** (5 nodes): `extractCwdResetWarning()`, `extractSandboxViolations()`, `removeSandboxViolationTags()`, `BashToolResultMessage.tsx`, `sandbox-ui-utils.ts`
  Too small to be a meaningful cluster - may be noise or needs more connections extracted.
- **Thin community `Community 44`** (5 nodes): `AnimatedClawd()`, `hold()`, `incrementFrame()`, `useClawdAnimation()`, `AnimatedClawd.tsx`
  Too small to be a meaningful cluster - may be noise or needs more connections extracted.
- **Thin community `Community 50`** (4 nodes): `getModelFamily()`, `resolveOpenAIModel()`, `modelMapping.ts`, `modelMapping.test.ts`
  Too small to be a meaningful cluster - may be noise or needs more connections extracted.

## Suggested Questions
_Questions this graph is uniquely positioned to answer:_

- **Why does `logForDebugging()` connect `Community 1` to `Community 0`, `Community 2`, `Community 3`, `Community 4`, `Community 5`, `Community 6`, `Community 7`, `Community 8`, `Community 9`, `Community 10`, `Community 11`, `Community 12`, `Community 13`, `Community 14`, `Community 15`, `Community 16`, `Community 17`, `Community 18`, `Community 19`, `Community 21`, `Community 22`, `Community 23`, `Community 24`, `Community 25`, `Community 26`, `Community 27`, `Community 29`, `Community 30`?**
  _High betweenness centrality (0.102) - this node is a cross-community bridge._
- **Why does `logEvent()` connect `Community 5` to `Community 0`, `Community 1`, `Community 2`, `Community 3`, `Community 4`, `Community 6`, `Community 7`, `Community 8`, `Community 9`, `Community 11`, `Community 12`, `Community 14`, `Community 15`, `Community 16`, `Community 17`, `Community 18`, `Community 19`, `Community 21`, `Community 22`, `Community 23`, `Community 26`, `Community 27`, `Community 29`, `Community 30`?**
  _High betweenness centrality (0.023) - this node is a cross-community bridge._
- **Why does `getGlobalConfig()` connect `Community 5` to `Community 1`, `Community 2`, `Community 3`, `Community 4`, `Community 6`, `Community 7`, `Community 8`, `Community 9`, `Community 11`, `Community 12`, `Community 14`, `Community 15`, `Community 16`, `Community 17`, `Community 18`, `Community 27`, `Community 31`?**
  _High betweenness centrality (0.021) - this node is a cross-community bridge._
- **Are the 793 inferred relationships involving `logForDebugging()` (e.g. with `immediateFlushHistory()` and `getSkills()`) actually correct?**
  _`logForDebugging()` has 793 INFERRED edges - model-reasoned connections that need verification._
- **Are the 337 inferred relationships involving `logError()` (e.g. with `loadSettingsFromFlag()` and `loadSettingSourcesFromFlag()`) actually correct?**
  _`logError()` has 337 INFERRED edges - model-reasoned connections that need verification._
- **Are the 339 inferred relationships involving `logEvent()` (e.g. with `logManagedSettings()` and `logStartupTelemetry()`) actually correct?**
  _`logEvent()` has 339 INFERRED edges - model-reasoned connections that need verification._
- **Are the 196 inferred relationships involving `jsonStringify()` (e.g. with `handleShutdownRequest()` and `handleShutdownApproval()`) actually correct?**
  _`jsonStringify()` has 196 INFERRED edges - model-reasoned connections that need verification._